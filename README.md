<!-- Você pode encontrar badges aqui: https://github.com/Ileriayo/markdown-badges?tab=readme-ov-file#markdown-badges -->
![Arduino](https://img.shields.io/badge/-Arduino-00979D?style=for-the-badge&logo=Arduino&logoColor=white)
![C++](https://img.shields.io/badge/c++-%2300599C.svg?style=for-the-badge&logo=c%2B%2B&logoColor=white)
![Java](https://img.shields.io/badge/java-%23ED8B00.svg?style=for-the-badge&logo=openjdk&logoColor=white)

---

#  Repositório dos Códigos do ProgramaCÃO


Este repositório contém o código para o projeto **ProgramaCÃO**, que monitora o nível de ração e água utilizando um sensor sônico e envia notificações via Telegram.

## Documentação

O projeto foi desenvolvido em C++ para a plataforma Arduino, utilizando bibliotecas específicas. É necessário instalar as versões das bibliotecas compatíveis com o código.

## Instalação

1. **Instale o Visual Studio**: [Link de download](https://visualstudio.microsoft.com/pt-br/#vs-section)
2. **Instale o Java**: [Link de download](https://www.java.com/pt-BR/download/ie_manual.jsp?locale=pt_BR)
3. **Instale o Arduino IDE**: [Link de download](https://www.arduino.cc/en/software)

Estas ferramentas são necessárias para rodar o código do ProgramaCÃO corretamente.

## Dependências

| Biblioteca               | Versão | Link para Documentação                                  |
| ------------------------ | ------ | ------------------------------------------------------ |
| ArduinoJson.h            | ?      | [Link](https://arduinojson.org)                         |
| ESP8266WiFi.h            | ?      | [Link](https://arduino-esp8266.readthedocs.io)         |
| UniversalTelegramBot.h   | ?      | [Link](https://github.com/witnessmenow/Universal-Arduino-Telegram-Bot) |
| WiFiClientSecure.h       | ?      | [Link](https://arduino-esp8266.readthedocs.io/en/latest/secureclient.html) |
| NewPing.h                | ?      | [Link](https://bitbucket.org/teckel12/arduino-new-ping/wiki/Home) |
| LCDWIKI_KBV.h            | 1.0    | [Link](http://www.lcdwiki.com/3.5inch_Arduino_Display-UNO#Program_Download) |

## Funcionalidades

- Monitoramento do nível de ração
- Notificações de nível de ração e água via Telegram
- Notificação crítica para grupo específico
- Sensor sônico para detectar o nível de ração
- Integração com o WiFi

## Funcionalidades Futuras

- Integração com API do WhatsApp

## Projetos Relacionados

Segue alguns projetos relacionados

- [Arduino on ESP8266](https://github.com/esp8266/Arduino)

## Referência

- [Java](https://www.java.com/pt-BR/download/ie_manual.jsp?locale=pt_BR) - Necessário para o funcionamento do Arduino IDE
- [Arduino IDE](https://www.arduino.cc/en/software) - Ambiente de desenvolvimento para Arduino
- [ArduinoJson](https://arduinojson.org/) - Biblioteca para manipulação de JSON no Arduino
- [ESP8266WiFi](https://arduino-esp8266.readthedocs.io/) - Biblioteca para conexão WiFi com ESP8266
- [Universal Telegram Bot](https://github.com/witnessmenow/Universal-Arduino-Telegram-Bot) - Biblioteca para comunicação com o Telegram
- [WiFiClientSecure](https://arduino-esp8266.readthedocs.io/en/latest/secureclient.html) - Cliente seguro para conexões WiFi
- [NewPing](https://bitbucket.org/teckel12/arduino-new-ping/wiki/Home) - Biblioteca para uso de sensores ultrassônicos
- [LCDWIKI_KBV](http://www.lcdwiki.com/3.5inch_Arduino_Display-UNO#Program_Download) - Biblioteca para displays LCD com Arduino

## FAQ 

### Como incluir as placas da família ESP8266 na Arduino IDE?

1. Acesse `Arquivo` > `Preferências`
2. Em `URLs adicionais para gerenciadores de placas`, insira o seguinte link:
   ```
   https://arduino.esp8266.com/stable/package_esp8266com_index.json
   ```

### Como encontrar a placa na IDE do Arduino?

1. Vá para `Ferramentas` > `Placa:` > `Gerenciador de Placas`
2. Pesquise e instale as placas ESP8266.

## Autores

- [@defaultdayanni](https://github.com/defaultdayanni)
