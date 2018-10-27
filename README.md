# o7t-greeting

oc new-project o7t-greeting  
oc project o7t-greeting

oc new-app \  
https://github.com/montebello64/o7t-greeting.git \  
--docker-image=montebello64/java-s2i \  
--context-dir=rest-name \  
--name=rest-name \  
-e SPRING_PROFILES_ACTIVE=openshift \  
-l microservice=o7t-greeting

oc expose service rest-name \  
--hostname=o7t-greeting-rest-name.zuggerschnecksche.de

oc new-app \  
https://github.com/montebello64/o7t-greeting.git \  
--docker-image=montebello64/java-s2i \  
--context-dir=rest-greeting \  
--name=rest-greeting \  
-e SPRING_PROFILES_ACTIVE=openshift \  
-l microservice=o7t-greeting

oc expose service rest-greeting \  
--hostname=o7t-greeting-rest-greeting.zuggerschnecksche.de

oc new-app \  
https://github.com/montebello64/o7t-greeting.git \  
--docker-image=montebello64/java-s2i \  
--context-dir=rest-consumer-gui \  
--name=rest-consumer-gui \  
-e SPRING_PROFILES_ACTIVE=openshift \  
-l microservice=o7t-greeting

oc expose service rest-consumer-gui \  
--hostname=o7t-greeting.zuggerschnecksche.de
