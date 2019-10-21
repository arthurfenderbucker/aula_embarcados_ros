# aula_embarcados_ros

[slides da aula](https://docs.google.com/presentation/d/1h9ojSn1rUXIYYMIOSQwRFE0Gco4dOe-2waOSVNG0w1I/edit?usp=sharing) (acessar com email usp)


#### simple ros commands:


#### tutoriais ROS:
http://wiki.ros.org/pt_BR/ROS/Tutorials

* [Writing a Simple Publisher and Subscriber (Python)](http://wiki.ros.org/ROS/Tutorials/WritingPublisherSubscriber%28python%29)
* [Writing a Simple Publisher and Subscriber (C++)](http://wiki.ros.org/ROS/Tutorials/WritingPublisherSubscriber%28c%2B%2B%29)



#### parte prática

* entre em https://rds.theconstructsim.com/r/
* crie uma conta gratis (sign up)
* Em NAME/DESCRIPTION procure por: [turtlebot](https://rds.theconstructsim.com/r/?search=turtlebot&ami=&order=-updated_on )
* clique em "Open" no primeiro resultado de "ROS_Basics_Project_Turtlebot" e aguarde o ambiente de trabalho ser criado
* feche o jupyter notebook
* em Tools clique clique em shell para abrir um terminal
* em Simulations clique em "choose launch file..", selecione no subitem "turtlebot_navegation_gazebo" o arquivo main.launch e clique em launch (use shift para e o botão direito mouse para navegar na simulação)
* explore o ambiente ros criado.<br>
no shell veja o resultado dos comando:
```
rosnode list  #running nodes
rostopic list #initialized topics

#existing packages related to "turtlebot" 
rospack list | grep turtlebot

rostopic echo /odom  #prints the result of the topic "/odom" (data from the odometry sensor)

#goes to the path of the specified ros package
roscd turtlebot_navigation_gazebo 
```
* veja a imagem que esta sendo transmitida pelo turtlebot. para isso, em Tools abra o "Camera Viewer". Execute os comandos sugeridos pela janela do camera viewer em 2 novos shells.
* em image topic selecione o topico da imagem que deseja ver (camera/rgb/image_raw ou camera/depth/image_raw)  
* agora tente controlar o robo por linha de comando
```
cd ~  #going back to the home folder

# velocity control
rostopic pub /cmd_vel geometry_msgs/Twist "linear:
  x: 0.3
  y: 0.0
  z: 0.0
angular:
  x: 0.0
  y: 0.0
  z: 0.0"

#use ctrl+C at the same shell to stop the transmission of the message

#to stop the robot you need to send a message with only zeros
rostopic pub /cmd_vel geometry_msgs/Twist "linear:
  x: 0.0
  y: 0.0
  z: 0.0
angular:
  x: 0.0
  y: 0.0
  z: 0.0"

#note that by using "tabs" while writing the command makes everything much easier
```

vamos agora escrever um node para controlar o robo de forma automatizada em python.
* entre no diretorio do workspace ```cd ~/catkin_ws``` e na subpasta que contem os pacotes ```cd src```.
* crie um pacote ```catkin_create_pkg O_NOME_Q_VC_QUISER std_msgs rospy roscpp``` (std_msgs,rospy e roscpp sao outros pacotes do ros que o seu pacote dependera, por hora não se preocupe com isso)
*note que o seu pacote foi criado, veja o seu conteudo ```ls O_NOME_Q_VC_QUISER```
* para criar um node nesse pacote: abra o IDE em Tools, e navegue até a pasta ~/catkin_ws/src/O_NOME_Q_VC_QUISER/src/ e crie um arquivo move_turtlebot.py
* insira nele o conteudo presente no arquivo move_turtlebot.py deste repositório e fique livre para modifica-lo (é só um exemplo)


referências:</br>
* http://www.ros.org
* http://wiki.ros.org
* http://courses.csail.mit.edu/6.141/spring2014/pub/lectures/Lec05-ROS-Lecture.pdf