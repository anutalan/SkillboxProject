## 14.1 Функциональное представление 

```mermaid
  graph TD;
  subgraph "Клиентская зона"
        Web[Клиентское Web приложение]
        Mobile[Клиентское мобильное приложение]
        AdminWeb[Web приложение поддержки]
        Платформа_IoT
        Онлайн_площадки_бренда       
  end
    
  subgraph "Демилитаризованная зона"
        Client_API_Gateway
        Web_BFF
        Mobile_BFF
        AdminWeb_BFF
        Auth
        Store_GateWay
        IoT_GateWay
  end
  
  subgraph "Внутренняя сеть"
    subgraph "Мониторинг"
        Prometheus
        PODS_Moниторинг
    end
        Platform_API_Gateway
        Сервис_Пользователей
        Сервис_Тренировок
        Сервис_Новостей_Рекламы
        Сервис_Устройств-датчиков
        Сервис_Онлайн_площадок_бренда
        Сервис_Уведомлений
        Сервис_Социальной_сети
        Сервис_Геймификации
        Prometheus       
        Кэш[(Кэш HazelCast)]
        BackToBackAuth      
    subgraph "Кластер Kafka"
        Брокер_Kafka
    end
    subgraph "Кластер БД"
        БДPrometheus[(БД Prometheus)]
        БДПользователей[(БД Пользоватей)]
        БДТренировок[(БД Тренировок)]
        БДНовостей[(БД Новостей)]
        БДУстройств[(БД Устройств)]
        БДОнлайн_площадок[(БД Площадок)]
        БДСоциальной_сети[(БД Соц_сети)]
        БДУведомлений[(БД Уведомлений)]
        БДГеймификации[(БД Геймификации)]
    end

  end
  
  Platform_API_Gateway-->Кэш
  Platform_API_Gateway-->BackToBackAuth
  Web -->Client_API_Gateway;
  Mobile -->Client_API_Gateway;
  AdminWeb -->Client_API_Gateway;
  Client_API_Gateway-->Web_BFF;
  Client_API_Gateway-->Mobile_BFF;
  Client_API_Gateway-->AdminWeb_BFF;
  Client_API_Gateway-->Auth;
  Web_BFF-->Platform_API_Gateway;
  Mobile_BFF-->Platform_API_Gateway;
  AdminWeb_BFF-->Platform_API_Gateway;
  
  
  Платформа_IoT-->IoT_GateWay;
  Сервис_Устройств-датчиков-->IoT_GateWay
  Онлайн_площадки_бренда-->Store_GateWay;
  Сервис_Уведомлений-->Сервис_Пользователей;  
  Сервис_Новостей_Рекламы-->Сервис_Пользователей;  
  
  IoT_GateWay-->Брокер_Kafka
  Сервис_Устройств-датчиков-->Брокер_Kafka
  Store_GateWay-->Брокер_Kafka;
  Сервис_Онлайн_площадок_бренда-->Брокер_Kafka;
  Сервис_Пользователей-->Брокер_Kafka;
  Сервис_Тренировок-->Брокер_Kafka;
  Сервис_Геймификации-->Брокер_Kafka;

  
  Platform_API_Gateway-->Сервис_Тренировок;
  Platform_API_Gateway-->Сервис_Социальной_сети;
  Platform_API_Gateway-->Сервис_Геймификации;
  Platform_API_Gateway-->Сервис_Новостей_Рекламы;
  Platform_API_Gateway-->Сервис_Пользователей;
  Platform_API_Gateway-->Сервис_Уведомлений;
  Platform_API_Gateway-->Сервис_Устройств-датчиков;
  Platform_API_Gateway-->Сервис_Онлайн_площадок_бренда;
  
 
   Prometheus-->PODS_Moниторинг;
    
   Сервис_Пользователей-->БДПользователей[(БД Пользоватей)]
   Сервис_Тренировок-->БДТренировок[(БД Тренировок)]
   Сервис_Новостей_Рекламы-->БДНовостей[(БД Новостей)]
   Сервис_Устройств-датчиков-->БДУстройств[(БД Устройств)]
   Сервис_Онлайн_площадок_бренда-->БДОнлайн_площадок[(БД Площадок)]
   Сервис_Уведомлений-->БДУведомлений[(БД Нотификации)]
   Сервис_Социальной_сети-->БДСоциальной_сети[(БД Соц_сети)]
   Сервис_Геймификации-->БДГеймификации[(БД Геймификации)]
   Prometheus-->БДPrometheus[(БД Prometheus)]
        
   style Prometheus fill:#e1f8fe
   style PODS_Moниторинг fill:#e1f8fe
   style Auth fill:#F0E68C
   style BackToBackAuth fill:#F0E68C
   style IoT_GateWay fill:#D8BFD8
   style Store_GateWay fill:#D8BFD8
   style Client_API_Gateway fill:#D8BFD8
   style Platform_API_Gateway fill:#D8BFD8
   style Web fill:#fff990
   style Mobile fill:#fff990
   style AdminWeb fill:#fff990   
   style Брокер_Kafka fill:#AFEEEE


 ```
