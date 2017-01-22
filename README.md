创建dubbo-registry-consul项目

resources创建META-INF.dubbo.internal目录，其中名为com.alibaba.dubbo.registry.RegistryFactory的文件，
内容为consul=com.alibaba.dubbo.registry.consul.ConsulRegistryFactory

ConsulRegistry extends FailbackRegistry
ConsulRegistryFactory  implements RegistryFactory

dubbo（全局）中添加依赖
<dependency>
            <groupId>com.alibaba</groupId>
            <artifactId>dubbo-registry-consul</artifactId>
            <version>${project.parent.version}</version>
 </dependency>

整体打包时包含
<include>com.alibaba:dubbo-registry-consul</include>


spring配置开启注册器标签
<dubbo:registry protocol="consul" address="192.168.43.78:8500"/>


开启注册标签后，ConsulRegistry构造器会实例化Consul客户端

服务配置时，启用consul注册中心
<dubbo:reference id="bidService" interface="com.alibaba.dubbo.demo.bid.BidService" registry="consul"/>

以上步骤会调用ConsulRegistry中doRegister方法
将服务注册到注册中心
