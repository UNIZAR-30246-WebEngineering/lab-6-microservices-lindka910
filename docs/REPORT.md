- Create your own configuration repository based on https://github.com/UNIZAR-30246-WebEngineering/lab6-microservices-config-repo 
and update the configuration of your service config to use it. 

- Link to the repository: https://github.com/lindka910/lab6-microservices-config-repo

- Two services accounts (2222) and web are running and registered (two terminals). **Log screenshot**.
  <br>
  <br>
  ![screen1_accounts.jpg](screenshots%2Fscreen1_accounts.jpg)
<br>
<br>
  ![screen2_webserver.jpg](screenshots%2Fscreen2_webserver.jpg)
<br>
<br>
- The service registration service has these two services registered (a third terminal). **Eureka dashboard screenshot**.
  ![screen3_dashboardEureka.jpg](screenshots%2Fscreen3_dashboardEureka.jpg)
<br>
<br>
- Update the configuration repository so that the accounts service uses now the port 3333. 
<br>**Link to the commit**:
  https://github.com/lindka910/lab6-microservices-config-repo/commit/a5e4bb275533e15a571f83cc029a4287c38d9d51
- Run a second instance of the accounts service using the new configuration (a fourth terminals).
**What happens? Explain and Eureka dashboard screenshot**<br>
  Updating the configuration in the repository and then starting a second instance of the account server with a new port (3333) has the following effects:
  - The second instance successfully registers with Eureka under the name "ACCOUNTS-SERVICE" with the updated port (3333).
  - The Eureka dashboard now shows two registered instances of the account service, one with the original port (2222) and one with the new port (3333).

  This update demonstrates the scalability of the microservices system and the ability to transparently implement changes in the configuration. Both instances of the account server can now process requests independently of each other, demonstrating the flexibility and ability to scale the system horizontally. 
    
  ![screen4_dashboard2.jpg](screenshots%2Fscreen4_dashboard2.jpg)
<br>
<br>
- What happens when you kill the service accounts (2222) and do requests to web?. **Explain and screenshots, including at least one Eureka dashboard screenshot**
  -  As shown in the screenshot the service (2222) is no longer registered. When the ACCOUNTS-SERVICE on port 2222 is terminated, Eureka updates its registry, triggering a failover. The web service, utilizing Eureka, redirects requests to the available ACCOUNTS-SERVICE instance, like the one on port 3333.
  ![screen5_dashboard3.jpg](screenshots%2Fscreen5_dashboard3.jpg)
<br>
<br>
- Can the web service provide information about the accounts again?. Why? **Explain and screenshots, including at least one Eureka dashboard screenshot**
  - Yes, the web service can provide information about accounts again. With the failover mechanism, the web service redirects requests to the available ACCOUNTS-SERVICE instance on port 3333. The system's resilience ensures continuity in delivering account information.
  ![screen6_requests.jpg](screenshots%2Fscreen6_requests.jpg)
<br>
<br>
  ![screen7_dashboard4.jpg](screenshots%2Fscreen7_dashboard4.jpg)
<br>
<br>
