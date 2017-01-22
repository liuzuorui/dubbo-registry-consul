基于
###dubbox：2.8.4<br>
###consul:0.7.0<br>

dubbo-registry项目下创建dubbo-registry-consul项目<br>

resources创建META-INF.dubbo.internal目录，其中名为com.alibaba.dubbo.registry.RegistryFactory的文件，<br>
内容为consul=com.alibaba.dubbo.registry.consul.ConsulRegistryFactory<br>

ConsulRegistry extends FailbackRegistry<br>
ConsulRegistryFactory  implements RegistryFactory<br>

dubbo项目中添加依赖<br>
### \<dependency>
###            \<groupId>com.alibaba\</groupId>
###            \<artifactId>dubbo-registry-consul\</artifactId>
###            \<version>${project.parent.version}\</version>
### \</dependency>

dubbo项目中整体打包时包含<br>
###\<include>com.alibaba:dubbo-registry-consul\</include>

consumer&provider demo项目中spring配置开启注册器标签<br>
###\<dubbo:registry protocol="consul" address="192.168.43.78:8500"/>

服务配置时，启用consul注册中心<br>
\<dubbo:reference id="bidService" interface="com.alibaba.dubbo.demo.bid.BidService" registry="consul"/>

