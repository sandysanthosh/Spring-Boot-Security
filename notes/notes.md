## Spring-Boot-Security


### Security:

        * Principal:

        - User, Device or system that perform an action

        * Authentication:

        - Establising that a principal credentials are valid

        * Authorization:

        -  Decidicing if principal is allowed to Perform an

        * Authority;

        - Permission or credential enabling access(such as role)

        * Secured Item:

        - Resource that is being Secured


#### Authentication:

       There are many authentication mechanisms:

       - Example:Basic, Digest, Form, X.509, OAuth

       There are many storage options for credential and authority information:

       - Example: in-memory(development), Databases, LDAP.

#### Authorization:

     Authorization depends on authentication

     - Before deciding if a user can perform an action, user identify must be established

       Authorization determines if you have the required Authoritu

       The decision process if often baed on roles:  

         * Admin can cancel orders

         * Member can place orders

         * Guest can browse the catalog


#### Spring Security Project:  

#### Portable:

       Secured archive(JAR,EAR,WAR) cam ne deployed as

#### Seperation of Concerns:

        Business logic is decoupled from security Concerns

        Authentication and Authorization are decoupled  ->  Changes to authentication have no impact on authorizations
               
  #### Flexible & Extensible:
  
      - Authentication ::Basic, Digest, Form, X.509, OAuth, Cookies, single-sign-On..

      - Storage: in-memory(development), Databases, LDAP, RDMS, properties file, custom DAOS..

      - Highly customizable
       
       
  
  
  
