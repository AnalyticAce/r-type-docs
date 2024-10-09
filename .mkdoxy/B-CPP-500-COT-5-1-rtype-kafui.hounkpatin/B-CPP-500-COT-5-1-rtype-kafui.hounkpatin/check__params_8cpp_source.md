

# File check\_params.cpp

[**File List**](files.md) **>** [**Server**](dir_f6675a7e1cd1d6d7f6e5e9669ead62e8.md) **>** [**src**](dir_35da1b20ef5d00fba1377c2ea4ffeb70.md) **>** [**check\_params.cpp**](check__params_8cpp.md)

[Go to the documentation of this file](check__params_8cpp.md)


```C++
/*
** EPITECH PROJECT, 2024
** check_param
** File description:
** check_params
*/

#include "../include/Server.hpp"

static const server_t CHECK_SERVER = {.tcp_port = -1, .udp_port = -1};

bool sup_int_spec(int *param, char **av) {
  if (!av || !av[0]) {
    return false;
  }
  try {
    *param = std::stoi(av[0]);
  } catch (const std::invalid_argument &) {
    return false;
  }
  return (*param > 0);
}

static const std::vector<parameter_t> ZAPPY_SERVER_PARAMS = {
    {"-tcp",
     [](int *param, char **av) -> bool { return sup_int_spec(param, av); },
     "tcp_port", "is the tcp port number",
     static_cast<int>(reinterpret_cast<const char *>(&CHECK_SERVER.tcp_port) -
                      reinterpret_cast<const char *>(&CHECK_SERVER))},
    {"-udp",
     [](int *param, char **av) -> bool { return sup_int_spec(param, av); },
     "udp_port", "is the udp port number",
     static_cast<int>(reinterpret_cast<const char *>(&CHECK_SERVER.udp_port) -
                      reinterpret_cast<const char *>(&CHECK_SERVER))}};

void usage() {
  std::cout << "USAGE: ./r_type_server -tcp tcp_port -udp udp_port\n"
               "tcp_port\tis the tcp port number\n"
               "udp_port\tis the udp port number\n";
  std::exit(0);
}

bool add_to_server_struct(server_t *server, char **av, int i) {
  for (const auto &param : ZAPPY_SERVER_PARAMS) {
    if (!strcmp(av[i], param.argument.c_str()) &&
        !param.add_new_param(
            reinterpret_cast<int *>(reinterpret_cast<char *>(server) +
                                    param.check_me),
            &av[i + 1])) {
      std::cerr << "Invalid " << param.name << "\n"
                << param.name << " " << param.usage << "\n";
      return false;
    }
  }
  return true;
}

void initialize_parameters(server_t *server) {
  server->tcp_port = 0;
  server->udp_port = 0;
}

bool recup_args(server_t *server, int ac, char **av) {
  initialize_parameters(server);
  for (int i = 0; i < ac; ++i) {
    if (!add_to_server_struct(server, av, i))
      return false;
  }
  if (server->tcp_port <= 0 || server->udp_port <= 0) {
    usage();
    return false;
  }
  return true;
}
```


