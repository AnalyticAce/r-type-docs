

# File robustness.cpp

[**File List**](files.md) **>** [**Server**](dir_f6675a7e1cd1d6d7f6e5e9669ead62e8.md) **>** [**robustness.cpp**](robustness_8cpp.md)

[Go to the documentation of this file](robustness_8cpp.md)


```C++
/*
** EPITECH PROJECT, 2024
** B-CPP-500-COT-5-1-bsrtype-ilham.adios
** File description:
** robustness
*/

#include "../../include/Server/Server.hpp"

void Server::start_heartbeat_monitor(boost::asio::io_context &io_context)
{
    std::thread(
        [this, &io_context]()
        {
            while (true)
            {
                auto now = std::chrono::steady_clock::now();
                for (auto it = clients_me.begin(); it != clients_me.end();)
                {
                    auto time_since_last_ping = std::chrono::duration_cast<std::chrono::seconds>(
                        now - it->second.last_ping);
                    if (time_since_last_ping.count() > 10)
                    {
                        notify_clients_of_disconnection(io_context, it->first);
                        it = clients_me.erase(it);
                    }
                    else
                    {
                        ++it;
                    }
                }
                std::this_thread::sleep_for(std::chrono::seconds(1));
            }
        })
        .detach();
}

void Server::handle_client_ping(const udp::endpoint &client_endpoint)
{
    auto now = std::chrono::steady_clock::now();
    if (clients_me.find(client_endpoint) != clients_me.end())
    {
        clients_me[client_endpoint].last_ping = now;
    }
    else
    {
        clients_me[client_endpoint] = {now};
    }
    std::cout << "Updated ping for client: " << client_endpoint.address().to_string() << std::endl;
}

void Server::send_udp_with_ack(udp::socket &socket, const std::vector<uint8_t> &message,
                               const udp::endpoint &client_endpoint)
{
    int retry_count = 0;
    bool ack_received = false;

    while (retry_count < 3 && !ack_received)
    {
        socket.send_to(boost::asio::buffer(message), client_endpoint);
        std::cout << "Sent UDP message to client: " << client_endpoint.address().to_string()
                  << std::endl;

        std::array<uint8_t, 128> recv_buffer;
        udp::endpoint remote_endpoint;
        boost::system::error_code error;
        socket.receive_from(boost::asio::buffer(recv_buffer), remote_endpoint, 0, error);

        if (!error && recv_buffer[0] == 'A' && recv_buffer[1] == 'C' && recv_buffer[2] == 'K')
        {
            ack_received = true;
            std::cout << "Received ACK from client: " << client_endpoint.address().to_string()
                      << std::endl;
        }
        else
        {
            retry_count++;
            std::cout << "Retrying... Attempt: " << retry_count << std::endl;
        }
    }
    if (!ack_received)
    {
        std::cerr << "Failed to receive ACK after 3 attempts." << std::endl;
    }
}

void Server::notify_clients_of_disconnection(boost::asio::io_context &io_context,
                                             const udp::endpoint &disconnected_client)
{
    for (const auto &client : clients_me)
    {
        if (client.first != disconnected_client)
        {
            try
            {
                udp::socket socket(io_context, client.first.address().is_v6()
                                                   ? boost::asio::ip::udp::v6()
                                                   : boost::asio::ip::udp::v4());
                int socketfd = static_cast<int>(socket.native_handle());
                std::string message = "Client " + std::to_string(socketfd) + " has disconnected.";
                std::cout << message << std::endl;
                std::vector<uint8_t> message_data(message.begin(), message.end());
                socket.send_to(boost::asio::buffer(message_data), client.first);
                std::cout << "Notified clients: " << "About the disconnection of client "
                          << socketfd << std::endl;
            }
            catch (const std::exception &e)
            {
                std::cerr << "Error notifying client: " << client.first.address().to_string()
                          << " - " << e.what() << std::endl;
            }
        }
    }
}
```


