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
--hostname=rest-name.zuggerschnecksche.de

oc new-app \  
https://github.com/montebello64/o7t-greeting.git \  
--docker-image=montebello64/java-s2i \  
--context-dir=rest-greeting \  
--name=rest-greeting \  
-e SPRING_PROFILES_ACTIVE=openshift \  
-l microservice=o7t-greeting

oc expose service rest-greeting \  
--hostname=rest-greeting.zuggerschnecksche.de

oc new-app \  
https://github.com/montebello64/o7t-greeting.git \  
--docker-image=montebello64/java-s2i \  
--context-dir=rest-consumer-gui \  
--name=rest-consumer-gui \  
-e SPRING_PROFILES_ACTIVE=openshift \  
-l microservice=o7t-greeting

oc expose service rest-consumer-gui \  
--hostname=rest-consumer-gui.zuggerschnecksche.de
