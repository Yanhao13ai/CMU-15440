# CMU-15440
http://www.composablesystems.org/15-440/fa2024/<br />
### Introduction
when does a decentralized system become distributed? in general, adding k>0 links bt two nodes in a decentralized system, alternative approach exists when 2 views on realizing distributed systems: integrative view -connecting existing networked computer systems into a larger system, expansive view -an existing networked computer systems is extended with additional computers, hence, 2 definitions: a decentralized system is a networked computer system in which processes and resources are necessarily spread across multiple computers, a distributed system is a networked computer system in which processes and resources are sufficiently spread across multiple computers;<br /><br />
some common misconceptions including: centralized solutions do not scale -make distinction bt logically and physically centralized, the root of dns including: logically centralized, physically(massively) distributed, decentralized across several organizations; centralized solutions have a single point of failure -generally not true such as the root of dns, a single point of failure is often easier to manage, and easier to make more robust; note: there are many, poorly founded, misconceptions regarding scalability, fault tolerance, security, etc., we need to develop skills by which distributed systems can be readily understood so as to judge such misconceptions;<br /><br />
distributed systems are complex taking perspectives of: architecture -common organizations, process -what kind of processes and their relationships, comm -facilities for exchanging data, coordination -application-independent algorithms, naming -how do you identify resources?, consistency and replication -performance requires of data which need to be the same, fault tolerance -keep running in the presence of partial failures, security -ensure authorized access to resources;<br /><br />
what do we want to achieve? overall design goals including: support sharing of resources, distribution transparency, openness, scalability;<br /><br />
sharing resources: canonnical examples including: cloud-based shared storage and files, p2p assisted multimedia streaming, shared mail services such as outsourced mail systems, shared web hosting such as content distribution networks; observation -“the network is the computer,” quote from John Gage, then at Sun Microsystems;<br /><br />
distribution transparency: transparency -the phenomenon by which a distributed system attempts to hide the fact that its processes and resources are physically distributed across multiple computers, possibly separated by large distances; observation -distribution transparency is handled through many different techniques in a layer bt applications and os, i.e., a middleware layer; types including: access -hide differences in data representation and how an object is accessed, location -hide where an object is located, relocation -hide that an object may be moved to another location while in use, migration -hide that an object may move to another location, replication -hide that an object is replicated, concurrency -hide that an object may be shared by several independent users, failure -hide the failure and recovery of an object;<br /><br />
degree of transparency including: (i) aiming at full distribution transparency may be too much: there are comm latencies that cannot be hidden; completely hiding failures of networks and nodes is(theoretically and practically) impossible, i.e., you cannot distinguish a slow computer from a failing one, and you cannot be sure that a server actually performed an op before a crash; full transparency will cost perf, exposing distribution of the system, i.e., keeping replicas exactly up-to-date with the master takes time, and immediately flushing write op to disk for fault tolerance;<br /><br />
(ii) exposing distribution may be too good: making use of location-based services -finding your nearby friends, when dealing with users in different time zones, when it makes it easier for a user to understand what's going on -when for example, a server does not respond for a long time, report it as failing; conclusion -distribution transparency is a nice goal, but achieving it is a different story, and it should often not even be aimed at;<br /><br />
openness of distributed systems: open -a system that offers components that can easily be used by, or integrated into other systems, an open distributed system itself will often consist of components that originate from elsewhere; what are we talking about? be able to interact with services from other open systems, irrespective of the underlying environment -systems should be conform to well-defined interfaces, systems should be easily interoperate, systems should support portability of applications, systems should be easily extensible;<br /><br />
policies vs. mechanisms: policies including: what level of consistency do we require for client-based data? which op do we allow downloaded code to perform? which qos requirements do we adjust in the face of varying bandwidth? what level of secrecy do we require for comm? mechanisms including: allow (dynamic) setting of caching policies, support different levels of trust for mobile code, provide adjustable qos params per data stream, offer different encryption algorithms;<br /><br />
on strict separation: observation -the stricter the separation bt policy and mechanism, the more we need to ensure proper mechanisms, potentially leading to many config params and complex mgt; finding a balance -hard-coding policies often simplifies mgt, and reduces complexity at the price of less flexibility, there is no obvious solution;<br /><br />
一些常见的误解包括：集中式解决方案不具备扩展性 - 区分逻辑集中式和物理集中式，DNS 的根源包括：逻辑上集中式，物理上（大规模）分布式，跨多个组织分散式；集中式解决方案具有单点故障 - 一般情况并非如此，例如 DNS 的根源，单点故障通常更易于管理，并且更容易变得更加稳健；注意：关于可扩展性、容错性、安全性等，存在许多毫无根据的误解，我们需要培养能够轻松理解分布式系统的技能，以便判断这些误解；<br /><br />
分布式系统很复杂，从以下角度来看：架构-通用组织、流程-什么样的流程及其关系、通信-交换数据的设施、协调-独立于应用程序的算法、命名-如何识别资源？、一致性和复制-需要相同的数据的性能要求、容错性-在部分故障的情况下保持运行、安全性-确保对资源的授权访问；<br /><br />
我们想要实现什么？总体设计目标包括：支持资源共享、分发透明度、开放性、可扩展性；<br /><br />
共享资源：典型示例包括：基于云的共享存储和文件、p2p辅助多媒体流、共享邮件服务（如外包邮件系统）、共享网络托管（如内容分发网络）；观察 -“网络就是计算机”，引用当时在 Sun Microsystems 工作的 John Gage 的话；<br /><br />
分布透明度：透明度 - 分布式系统试图隐藏其进程和资源在物理上分布在多台计算机上的事实的现象，这些计算机可能相隔很远；观察 - 分布透明度通过应用程序和操作系统层（即中间件层）中的许多不同技术来处理；类型包括：访问 - 隐藏数据表示和对象访问方式的差异，位置 - 隐藏对象所在的位置，重定位 - 隐藏对象在使用时可能被移动到另一个位置，迁移 - 隐藏对象可能移动到另一个位置，复制 - 隐藏对象被复制，并发 - 隐藏对象可能由多个独立用户共享，故障 - 隐藏对象的故障和恢复；<br /><br />
透明度程度包括：(i) 旨在实现完全分布透明度可能太多：存在无法隐藏的通信延迟；完全隐藏网络和节点故障（在理论上和实践上）是不可能的，即你无法区分运行缓慢的计算机和发生故障的计算机，也无法确定服务器在崩溃前是否真正执行了操作；完全透明会降低性能，暴露系统的分布，即保持副本与主服务器完全同步需要时间，并且为了容错，会立即将写入操作刷新到磁盘；<br /><br />
(ii) 暴露分布可能太好了：利用基于位置的服务 - 找到你附近的朋友，当与不同时区的用户打交道时，当它使用户更容易了解发生了什么时 - 例如，当服务器长时间没有响应时，报告它为故障；结论 - 分布透明性是一个不错的目标，但实现它是另一回事，而且通常甚至不应该以此为目标；<br /><br />
分布式系统的开放性：开放 - 提供可轻松使用或集成到其他系统的组件的系统，开放的分布式系统本身通常由来自其他地方的组件组成；我们在说什么？能够与其他开放系统的服务进行交互，而不管底层环境如何 - 系统应符合定义良好的接口，系统应易于互操作，系统应支持应用程序的可移植性，系统应易于扩展；<br /><br />
政策与机制：政策包括：我们需要客户端数据的什么级别的一致性？我们允许下载的代码执行哪些操作？面对变化的带宽，我们要调整哪些 QoS 要求？我们需要什么级别的通信保密性？机制包括：允许（动态）设置缓存策略、支持不同级别的移动代码信任、为每个数据流提供可调整的 QoS 参数、提供不同的加密算法；<br /><br />
关于严格分离：观察 - BT 策略和机制分离越严格，我们越需要确保适当的机制，这可能会导致许多配置参数和复杂的管理；找到平衡点 - 硬编码策略通常会简化管理，并以灵活性较低为代价降低复杂性，没有明显的解决方案；<br /><br />
****
dependability: a component provides services to clients; to provide services, the component may require the services from other components -a component may depend on some other component; specifically, a component *C* depends on *C** if the correctness of *C*'s behavior depends on the correctness of *C**'s behavior, here, components are processes or channels; requirements related to dependability including: availability -readiness for usage, reliability -continuity of service delivery, safety -very low prob of catastrophes, maintainability -how easy can a failed system be repaired;<br /><br />
reliability vs. availability: reliability *R(t)* of component *C* -conditional prob that *C* has been functioning correctly during *[0,t)* given *C* was functioning correctly at time *T=0*; traditional metrics including: MTTF, MTTR, MTBF=MTTF+MTBF, here mean time to failure -the average time until a component fails, mean time to repaire -the average time needed to repair a component, mean time bt failures; terminology: failure -a component is not living up to its specifications such as crashed prog, error -part of a component that can lead to a failure such as prog bug, fault -cause of an error such as sloppy programmer, (handling faults including:) fault prevention -prevent the occurance of a fault such as do not hire sloppy programmers, fault tolerance -build a component and make it mask the occurance of a fault such as building each component by 2 independent programmers, fault removal -reduce the presence, number, or seriousness of a fault, such as getting rid of sloppy programmers, fault forecasting -estimate current presence, future incidence, and consequences of faults, such as estimating how a recruiter is doing when it comes to hiring sloppy programmers;<br /><br />
on security: observation -a distributed system that is not secure, is not dependable; what we need? confidentiality -info is disclosed only to authorized parties, integrity -ensure that alterations to assets of a system can be made only in an authorized way; authorization -verifying the correctness of a claimed identity, authentication -does an identified entity has proper access rights?, trust -one entity can be assured that another will perform particular actions according to a specific expectation;<br /><br />
security mechanisms: (i) keeping it simple: it is all about encrypting and decrypting data using security keys;<br /><br />
(ii) notation: *K(data)* denotes that we use key K to encrypt and decrypt data;<br /><br />
(iii) symmetric cryptosystem: with encryption key *E_K(data)* and decryption key *D_K(data)*, if *data=D_K(E_K(data))* then *D_K=E_K*, note: encryption and decryption key are the same and should be kept secret; asymmetric cryptosystem: distinguish a public key *PK(data)* and a private secret key *SK(data)* -encrypt msg from Alice to Bob as *data=SK_bob(data)*, sign msg for Bob by Alice as *[data,data=PK_alice(SK_alice(data))]=[data,SK_alice(data)]*;<br /><br />
(iv) secure hashing: in practice, we use secure hash functions -*H(data)* returns a fixed-length string, hence, any change from *data* to *data** will lead to a completely different string *H(data*)*, given a hash value, it is computationally impossible to find a data with *h=H(data)*;<br /><br />
(v) practical digital signatures: sign msg for Bob by Alice as *[data,H(data)=PK_alice(sgn)]=[data,H,sgn=SK_alice(H(data))]*;<br /><br />
scale in distributed systems: at least 3 components including: #users or processes -size scalability, max distance bt nodes -geographical scalability, #administrative domains -administrative scalability; observation -most systems account only for size scalability, often a solution -multiple powerful servers operating independently in parallel, today, the challenge still lies in geographical and administrative scalability;<br /><br />
size scalability: (i)root causes for scalability problems with centralized solutions including: the computational capacity, limited by cpus; the storage capacity, incorporating the transfer rate bt cpus and disks; the network bt user and centralized service;<br /><br />
(ii) [formal analysis, click to view](https://Yanhao13ai.github.io/CMU-15440/)<br /><br />
problems with geographical scalability including: cannot simply go from LAN to WAN -many distirbuted systems assume synchronous client-server interactions, where client sends req and waits for an answer, with latency may easily prohibit this scheme; WAN links are often inherently unreliable -simply moving streaming video from LAN to WAN is bound to fail; lack of multipoint comm, so that a simple search broadcast cannot be deployed, solution -develop separate naming and dir services(having their own scalability problems);<br /><br />
problems with administrative scalability: essence -conflicting policies concerning usage(and thus payment), mgt, and security; examples including: computational grids -share expensive resources bt different domains, shared equipment -how to control, manage, and use a shared radio telescope constructed as large-scale shared sensor network?; exception -several p2p networks including: file-sharing systems -based, such as on bittorrent, p2p telephony -early versions of skype, peer-assisted audio streaming -such as spotify, note: end users collaborate and not administrative entities collaborate;<br /><br />
techniques for scaling including: hide comm latencies -make use of asynchronous comm, have separate handler for incoming response, problem -not every application fits this model; facilitate solution by moving computations to client; partition data and computations across multiple machines -move computations to clients such as java applets and scripts, decentralized naming services such as dns, decentralized info systems such as www; replication and caching by making copies of data available at different machines -replicated file servers and db, mirrored websites, web caches(in browsers and proxies), file caching(at server and client);<br /><br />
scaling is the problem with replication, applying replication is easy, except for one thing: having multiple copies(cached or replicated) leads to inconsistencies -modifying one copy makes that copy different from the rest, always keeping copies consistent and in a general way requires global synchronization on each modification, global synchronization precludes large-scale solutions; observation -if we can tolerate inconsistencies, we may reduce the need for global synchronization, but tolerating inconsistencies is application dependent;<br /><br />
parallel computing: observation -hp distributed computing started with parallel computing; multiprocessor and multicore vs. multicomputer: former is shared mem--interconnect--processor, latter is mem--processor--interconnect;<br /><br />
distributed shared mem systems: observation -multiprocessors are relatively easy to program in comparison to multicomputers, yet have problems when increasing #processors(or cores), solution -implement a shared-mem model on top of a multicomputer; example through vm techniques -map all main-mem pages(from different processors) into 1 single virtual addr space, if a process at processor *A* addresses a page *P* located at processor *B*, os at *A* traps and fetches *P* from *B*, just as it would if *P* had been located on local stack; problem -perf of distributed shared mem could never compete with that of multprocessors, and failed to meet the exp of programmers, it has been widely abandoned by now;<br /><br />
[cluster computing, click to view](./img/cluster-computing.png): essentially a group of high-end systems connected through a LAN, it is (i)homogeneous -same os, near-identical hardware; (ii)single, or tightly coupled managing nodes;<br /><br />
[grid computing, click for architecture](./img/grid-computing-architecture.png): the next step -plenty of nodes from everywhere, it is (i)heterogeneous; (ii)desperseed across several organizations; (iii)can easily span a wide-area network; note: to allow for collaborations, grids generally use virtual org, in essence, this is a grouping of users(or better, their IDs) that allows for authorization on resource allocation;<br /><br />
integrating applications: situation -org confronted with many networked applications, but achieving interoperability was painful; basic approach -a networked application is one that runs on a server making its services available to remote clients, simple integration -clients combine reqs for (different) applications --> send that off --> collect responses, and present a coherent result to user; next step -allow direct application-to-application comm, leading to EAI -enterprise application integration:<br /><br />
example EAI: (nested) transactions: (i) transaction -primitive&description: BEGIN_TRANSACTION -mark the start of a transaction, END_TRANSACTION -terminate the transaction and try to commit, ABORT_TRANSACTION -kill the transaction and restore the old values, READ -read data from a file, a table, or otherwise, WRITE -write data to a file, a table, or otherwise;<br /><br />
(ii) [issue -all-or-nothing, click to view](./img/enterprise_application_integration-issue.png): it is atomic -happens indivisibly(seemingly), consistent -does not violate system invariants, isolated -not mutual interference, durable -commit means changes are permanent;<br /><br />
[TPM -transaction processing monitor, click to view](./img/transaction-processing-monitor.png): observation -often the data involved in a transaction is distributed across several servers, a tp monitor is responsible for coordinating the exec of a transaction;<br /><br />
[middleware and EAI, click to view](./img/middleware-and-enterprise_application_integration.png): middleware offers comm facilities for integration including: RPC -remote procedure call -reqs are sent through local procedure call, packaged as msg, processed, responded through msg, and result returned as return from call; MOM -msg oriented middleware -msg are sent to logical contact point(published), and forwarded to subscribed applications;<br /><br />
how to integrate applications? including: file transfer -technically simple but not flexible, (i)figure out file format and layout, (ii)figure out file mgt, (iii)update propagation and update notifications; shared db -much more flexible but still requires common data scheme next to risk of bottleneck; rpc -effective when exec of a series of actions is needed; messaging -rpc requires caller and callee to be up and running at the same time, messaging allows decoupling in time and space;<br /><br />
distributed pervasive systems: observation -emerging next-gen of distributed systems in which nodes are small, mobile, and often embedded in a larger system, characterized by the fact that the system naturally blends into the user's environment; 3 (overlapping) subtypes including: ubiquitous computing systems -pervasive and continuously present, i.e., there is a continuous interaction bt system and user; mobile computing systems -pervasive, but emphasis is on the fact that devices are inherently mobile; sensor (and actuator) networks -pervasive, with emphasis on the actual (collaborative) sensing and actuation of the environent;<br /><br />
ubiquitous systems: core elements including: distribution -devices are networked distributed and accessible transparently, interaction -interaction bt users and devices is highly unobtrusive, context awareness -system is aware of a user's context to optimize interaction, autonomy -devices operate autonomously without human intervention and are hence highly self-managed, intelligence -system as a whole can handle a wide range of dynamic actions and interactions;<br /><br />
[mobile computing, click to view](./img/mobile-computing.png): it is (i)a myriad of different mobile devices of smartphones, tablets, gps devices, remote controls, active badges, (ii)mobile implies that a device's location is exep to change over time, hence, change of local services, reachability, etc., keyword is discovery, (iii)maintaining stable comm can introduce serious problems, (iv)for a long time, research has focused on directly sharing resources bt mobile devices, it never became popular and is by now considered to be a fruitless path for research; bottomline -mobile devices set up connections to stationary servers, essentially bringing mobile computing in the position of clients of cloud-based services;<br /><br />
sensor networks: the nodes to which sensors are attached are many(10s-1000s), simple(small mem/compute/comm capacity), often battery-powered(or even battery-less); [sensor networks as distributed db, click for 2 extremes](./img/sensor_networks_as_distributed_db-extreme.png); [the cloud-edge continuum, click for continuum](./img/cloud-edge-continuum.png);<br /><br />
developing distributed systems: pitfalls: observation -many distributed systems are needlessly complex, caused by mistakes that required patching later on, many false assumptions are often made; false (and often hidden) assumptions including: the network is reliable, the network is secure, the network is homogeneous, the topology does not change, latency is zero, bdwidth is zero, transport cost is zero, there is 1 administrator;<br /><br />
地理可扩展性问题包括：不能简单地从 LAN 转到 WAN - 许多分布式系统假设同步客户端-服务器交互，客户端发送请求并等待答复，延迟可能很容易阻止这种方案；WAN 链接通常本质上不可靠 - 简单地将流视频从 LAN 移动到 WAN 注定会失败；缺乏多点通信，因此无法部署简单的搜索广播，解决方案 - 开发单独的命名和目录服务（具有自己的可扩展性问题）；<br /><br />
管理可扩展性问题：本质 - 有关使用（以及付款）、管理和安全性的冲突政策；示例包括：计算网格 - 在不同域、共享设备之间共享昂贵的资源 - 如何控制、管理和使用构建为大规模共享传感器网络的共享射电望远镜？；例外 - 几个 p2p 网络包括：基于文件共享系统，例如 bittorrent、p2p 电话 -skype 的早期版本、对等辅助音频流 -例如 spotify，注意：最终用户协作而不是管理实体协作；<br /><br />
扩展技术包括：隐藏通信延迟 - 使用异步通信，对传入响应有单独的处理程序，问题 - 并非每个应用程序都适合此模型；通过将计算移动到客户端来促进解决方案；在多台机器上划分数据和计算 - 将计算移动到客户端，例如 java 小程序和脚本、分散命名服务（例如 dns）、分散信息系统（例如 www）；通过在不同的机器上提供数据副本来实现复制和缓存 - 复制文件服务器和数据库、镜像网站、Web 缓存（在浏览器和代理中）、文件缓存（在服务器和客户端）；<br /><br />
扩展是复制的问题，应用复制很容易，但有一点除外：拥有多个副本（缓存或复制）会导致不一致 - 修改一个副本会使该副本与其他副本不同，始终保持副本一致，并且通常需要对每次修改进行全局同步，全局同步会排除大规模解决方案；观察 - 如果我们能够容忍不一致，我们可能会减少对全局同步的需求，但容忍不一致取决于应用程序；<br /><br />
并行计算：观察 -hp 分布式计算始于并行计算；多处理器和多核与多计算机：前者是共享内存-互连-处理器，后者是内存-处理器-互连；<br /><br />
分布式共享内存系统：观察 - 与多计算机相比，多处理器相对容易编程，但在增加处理器（或核心）数量时会出现问题，解决方案 - 在多计算机之上实现共享内存模型；例如通过虚拟机技术 - 将所有主内存页面（来自不同的处理器）映射到 1 个虚拟地址空间，如果处理器 *A* 上的进程寻址位于处理器 *B* 上的页面 *P*，则 *A* 上的操作系统会从 *B* 捕获并获取 *P*，就像 *P* 位于本地堆栈上一样；问题 - 分布式共享内存的性能永远无法与多处理器相媲美，也无法满足程序员的需要，因此现在已被广泛抛弃；<br /><br />
[集群计算，点击查看](./img/cluster-computing.png)：本质上是一组通过 LAN 连接的高端系统，它是 (i) 同质的 - 相同的操作系统，几乎相同的硬件；(ii) 单一或紧密耦合的管理节点；<br /><br />
[网格计算，点击查看架构](./img/grid-computing-architecture.png)：下一步 - 来自各处的大量节点，它是 (i) 异构的；(ii) 分散在多个组织中；(iii) 可以轻松跨越广域网；注意：为了实现协作，网格通常使用虚拟组织，本质上，这是一组用户（或更好的是他们的 ID）的分组，允许对资源分配进行授权；<br /><br />
集成应用程序：情况 - 组织面临许多联网应用程序，但实现互操作性却很痛苦；基本方法 - 联网应用程序是在服务器上运行的应用程序，使其服务可供远程客户端使用，简单集成 - 客户端组合（不同）应用程序的请求 --> 发送 --> 收集响应，并向用户呈现连贯的结果；下一步 - 允许直接应用程序到应用程序通信，从而实现 EAI - 企业应用程序集成：<br /><br />
示例 EAI：（嵌套）事务：(i) 事务 - 原始和说明：BEGIN_TRANSACTION - 标记事务的开始，END_TRANSACTION - 终止事务并尝试提交，ABORT_TRANSACTION - 终止事务并恢复旧值，READ - 从文件、表或其他位置读取数据，WRITE - 将数据写入文件、表或其他位置；<br /><br />
(ii) [问题 - 全有或全无，单击查看](./img/enterprise_application_integration-issue.png)：它是原子 -不可分割地发生（表面上），一致 -不违反系统不变量，隔离 -不相互干扰，持久 -提交意味着更改是永久性的；<br /><br />
[TPM -事务处理监视器，单击查看](./img/transaction-processing-monitor.png)：观察 -通常，事务中涉及的数据分布在多个服务器上，TP监视器负责协调事务的执行；<br /><br />
[中间件和EAI，单击查看](./img/middleware-and-enterprise_application_integration.png)：中间件为集成提供通信设施，包括：RPC -远程过程调用 -请求通过本地过程调用发送，打包为消息，处理，通过消息响应，并将结果作为调用返回； MOM - 面向消息的中间件 - 消息被发送到逻辑接触点（已发布），并转发给订阅的应用程序；<br /><br />
如何集成应用程序？包括：文件传输 - 技术上简单但不灵活，（i）弄清楚文件格式和布局，（ii）弄清楚文件管理，（iii）更新传播和更新通知；共享数据库 - 更灵活，但仍然需要通用数据方案，否则存在瓶颈风险；rpc - 在需要执行一系列操作时有效；消息传递 -rpc 要求调用者和被调用者同时启动和运行，消息传递允许在时间和空间上解耦；<br /><br />
分布式普适系统：观察 - 新兴的下一代分布式系统，其中节点很小、可移动，并且通常嵌入在更大的系统中，其特点是系统自然融入用户的环境； 3 种（重叠）子类型包括：普适计算系统 - 无处不在且持续存在，即系统和用户之间存在持续的交互；移动计算系统 - 无处不在，但重点在于设备本质上是移动的；传感器（和执行器）网络 - 无处不在，重点是环境的实际（协作）感知和驱动；<br /><br />
无处不在的系统：核心元素包括：分布 - 设备联网分布且透明可访问，交互 - 用户和设备之间的交互非常不引人注目，情境感知 - 系统了解用户情境以优化交互，自主性 - 设备自主运行而无需人工干预，因此高度自我管理，智能 - 整个系统可以处理各种动态操作和交互；<br /><br />
[移动计算，单击查看](./img/mobile-computing.png)：它是 (i) 智能手机、平板电脑、gps 设备、遥控器、活动徽章等各种移动设备，(ii) 移动意味着设备的位置可以随时间变化，因此本地服务、可达性等会发生变化，关键词是发现，(iii) 维持稳定的通信可能会引发严重问题， (iv)长期以来，研究一直专注于直接通过移动设备共享资源，但这种做法从未流行起来，目前被认为是一条徒劳的研究之路；底线——移动设备与固定服务器建立连接，本质上将移动计算置于基于云的服务的客户端位置；<br /><br />
传感器网络：传感器连接的节点很多（10-1000 个），简单（内存/计算/通信容量小），通常由电池供电（甚至无电池）；[传感器网络作为分布式数据库，单击可查看 2 个极端](./img/sensor_networks_as_distributed_db-extreme.png)；[云边缘连续体，单击可查看连续体](./img/cloud-edge-continuum.png)；<br /><br />
开发分布式系统：陷阱：观察——许多分布式系统不必要地复杂，这是由需要稍后修补的错误引起的，通常会做出许多错误的假设；错误的（通常是隐藏的）假设包括：网络是可靠的、网络是安全的、网络是同质的、拓扑结构不变、延迟为零、带宽为零、传输成本为零、有 1 个管理员；<br /><br />
****





