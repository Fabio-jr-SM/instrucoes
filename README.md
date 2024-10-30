# Repositório de Códigos - Projeto ProgramaCÃO
## Monitoramento de Nível de Ração e Água

Este projeto monitora o nível de ração e água de um recipiente utilizando sensores de distância, enviando notificações para um bot no Telegram em caso de mudança no nível ou necessidade de reposição.

## 📄 Documentação

O código está escrito em **C++** e utiliza bibliotecas para **Arduino** e o módulo **ESP8266** para conexão com o WiFi. As notificações são enviadas para um grupo e usuários específicos via **Telegram**.

### Principais Funcionalidades
- Monitora o nível da ração e água em um recipiente usando um sensor de distância (HC-SR04).
- Envia notificações via bot do Telegram quando o nível está cheio, acabando ou quando a tampa está aberta.
- Realiza uma verificação de nível de água a cada 3 dias e envia uma mensagem de lembrete.

## 🚀 Instalação e Configuração

1. **Instale as bibliotecas necessárias** para rodar o código no Arduino IDE:
   - **ArduinoJson**
   - **ESP8266WiFi**
   - **UniversalTelegramBot**
   - **WiFiClientSecure**
   - **NewPing**

2. **Configuração do WiFi**:
   - Modifique as variáveis `ssid` e `password` no código para a sua rede WiFi:
     ```cpp
     const char* ssid = "SuaRedeWiFi";
     const char* password = "SuaSenhaWiFi";
     ```

3. **Configuração do Bot do Telegram**:
   - Substitua o valor de `botToken` pelo token do seu bot no Telegram.
   - Configure `chatIdCritical` com o ID do grupo para alertas críticos.
   - Adicione os IDs dos chats que devem receber notificações gerais em `chatIdsGeneral`.

## 📚 Dependências

| Biblioteca              | Versão | Link para Download                     |
|-------------------------|--------|----------------------------------------|
| ArduinoJson             | 6.x    | [Download](https://arduinojson.org/)   |
| ESP8266WiFi             | 2.x    | [Download](https://github.com/esp8266/)|
| UniversalTelegramBot    | 1.3    | [Download](https://github.com/witnessmenow/Universal-Arduino-Telegram-Bot) |
| WiFiClientSecure        | 1.x    | Incluída no ESP8266 Core               |
| NewPing                 | 1.x    | [Download](https://bitbucket.org/teckel12/arduino-new-ping/wiki/Home) |

## ⚙️ Exemplo de Uso

1. **Conectar ao WiFi**: O ESP8266 se conecta automaticamente à rede WiFi configurada.
2. **Monitoramento do Recipiente**: O sensor de distância mede o nível da ração e da água, atualizando o estado e enviando notificações ao Telegram.
3. **Notificação de Verificação de Água**: A cada 3 dias, o bot envia uma mensagem solicitando verificação do nível de água.
