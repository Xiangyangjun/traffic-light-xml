# traffic-light-xml
使用uppaal软件实现基于交通灯的自动机
## uppaal
uppaal，是由瑞典的Uppsala大学信息技术系与丹麦的Aalborg大学计算机科学基础研究所联合研发的用于实时系统模拟、仿真和验证的工具。UPPAAL具有可视化的描述界面，使用方便高效
## 实验设计
        实验中所设计的交通灯包括两个进程：交通灯和行人，每个进程即是一个时间状态机。
    交通灯拥有两种模式：普通模式和行人模式。  
普通模式即交通灯三种灯不停的轮流转换，绿灯保持20秒，黄灯保持5秒，红灯保持20秒。  
行人模式是在有行人的情况下，交通灯为了照顾行人而优先行人通过，保证行人在进入交通路口后，无论何时只需等待五秒钟就可以通行。
这里的交通灯是对车辆而言，当交通灯为红色时，车辆停车等待，行人通行。    
    针对上述说明，我们对两个时间自动机分别赋予状态。  
交通灯拥有三个状态：绿灯，黄灯，红灯。  
行人拥有四个人状态：空闲状态idle，开始状态start，等待状态wait以及通行状态going。    
对于交通灯的两种模式，我们定义一个布尔型的变量activated，当其为真时代表交通灯处于行人模式，当其为假表示行人处于普通模式。当行人由空闲状态进入开始状态时，将activated置为真，表示行人开始进入路口，如果行人一直处于空闲状态，则activated始终为假，交通灯一直处于普通模式运作，即一直处于三种灯的不停轮换中。
为了保证两个状态机的同步，定义三个chan同步变量：enter，ready和finsh。enter变量表示行人进入路口，ready表示行人等待5秒以后开始通行，finsh表示行人完成通行。
