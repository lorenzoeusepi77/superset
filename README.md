# Docker image for Superset+LdapIntegration + DB Postgres + Redis

Follow this guide to install and run Superset docker image:

	git clone https://github.com/lorenzoeusepi77/superset.git

	cd superset



Configure LDAP parameters inside the configuration file "superset_config.py" before to build image. If you don't need LDAP auth you must comment the first line: 

	AUTH_TYPE = AUTH_LDAP
	AUTH_LDAP_SERVER = "ldaps://server:389"
	AUTH_LDAP_SEARCH = "cn=users,cn=accounts,dc=test,dc=example,dc=it"
	AUTH_LDAP_UID_FIELD = "uid"
	AUTH_LDAP_FIRSTNAME_FIELD = "givenName"
	AUTH_LDAP_LASTNAME_FIELD = "sn"
	AUTH_LDAP_EMAIL_FIELD = "mail"
	AUTH_LDAP_BIND_USER = "uid=admin,cn=users,cn=accounts,dc=test,dc=example,dc=it"
	AUTH_LDAP_BIND_PASSWORD = "password"
	AUTH_LDAP_ALLOW_SELF_SIGNED = True


#Build superset image

	./build.sh                           


#Start superset - postgres - redis

	docker-compose up -d                 


#First time to create admin user (User: admin Password: password) - initialize db - exmaple 

	./init.sh                            


Access to superset with your browser with this URL:PORT:

	http://localhost:8088

NOTE: You can login with local admin just if you don't have LDAP integration active.
