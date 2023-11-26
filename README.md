# System_Programming
It's just personal purpose only to learn and store my learning and Practice source codes.
To compile source code of linux kernel module we need to use command 'make' simply
To Check logs of kernel modules from the 'kern.log' file only cmd- 'tail -f /var/log/kern.log'
To insert module (file .ko) run command sudo insmod <file.ko>


Inserting a Module(Driver) 'sudo insmod file.ko'
removing a Module 'sudo rmmod file'
to check modules got inserted 'lsmod'


*************************************************************************************************

============Netlink Sokets===========

*	Netlink Sockets are especially designed to facilitate clean bidirectional communication between users and kernal space.
*	Other Techniques also can be used for US<>KS communication, but those technique were invented for the perpose. like Ioctls, device files, System calls.
*	But a Soket based technique was developed to build the unified interface using wich user space application (USA) can interact with various kernel subsystem.

	int skt_fd = socket(socket address Family, comunication type , protocol ID);

Project Details:
Communication between user space application and Routing Table Mgr (Kernal Subsystem)

USA(User Space Apllication) Action:
Perform CRUD operations.

KS(Kernel Space) Actions:
*	Write a Linux kernal Module which will behave as Routing Table MGr residing in kernel space.
*	It shall process CRUD orders coming from application.

Idea: To explore Netlink Socket based communication between US & KS by developing USA which interact with our LKM which is in-charge of our Routing Subsystem of Kerneli.


Netlink Messege format:

Netlink Msg Hadder(16B) Padding(fewBytes) Payload(msg)

struct nlnmsghdr{
		  u32 nlmsg_len;
		  u16 nlmsg_type;
		  u16 nlmsg_flags;
                  u32 nlmsg_seg;
                  u32 nlmsg_pid;
                }

