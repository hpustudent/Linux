### tengine 的配置
1. server 元素中将root目录设置为tomcat 的静态资源目录，root /usr/local/tomcat/webapps/项目名/WEB-INF

### tomcat 的配置
1. engine标签下添加Host标签，appBase表示自动部署的目录，docbase表示虚拟根目录，注意要使用全路径

        <Engine name="Catalina" defaultHost="localhost">
              <Realm className="org.apache.catalina.realm.LockOutRealm">
                <Realm className="org.apache.catalina.realm.UserDatabaseRealm"
                       resourceName="UserDatabase"/>
              </Realm>
              <Host name="localhost" appBase="webapps" unpackWARs="true" autoDeploy="true">
                <Context path="/" docBase="/usr/local/tomcat/webapps/articleserver" reloadable="true"/>
              </Host>
            </Engine>
