## Task 4: Learning about your client
[Notes 1.1 Systems in organizations](https://docs.google.com/document/d/1davsS5s6w4Gz3mCFDHJZwY53Eken14AIiKcCDPrY0Ig/edit#)
### Consider also the previous Matrix. The following is the description of the problem as described by the student that created it 2 years ago:

### “Currently, every time students go off-campus we have to sign out by filling out a Google Form. We specify our return date, destination, and other details. When we return back from our outing we sign in by checking our name out of a list of  signed-out people. The form is long (it has around 8 questions), it does not have any default input values (such as the date or destination), and many times the data is the same or unique for each user, for example, the house to which they belong to or their mobile phone. The “overnight” checkbox is another example of an unnecessary question: this can be calculated by parsingthe input return ate.”

### 1. What is the context in which the original Matrix system was designed?
  * How big did the Matrix system need to be? 
  * What features were needed?
  * Who were the intended users of the system?

The old Matrix system was designed to serve for the whole school community. For signing out, there was a Google form with around 8 questions to ask students their 
names, return date, destination, phone number, house,etc.. There were no default input values and "overnight" checkbox was an unecessary question as "this can be 
calculated by parsing input return date. For signing back in, students had to check their names out of a long list of signed-out people. Students are the users 
offering data while faculty are the users going through these data.

### 2. What are some issues that could arise when transitioning from the old sign in/out system based on Google Forms to the dedicated web application Matrix? 
1. Information security. When the data are moved to a web application Matrix, there's log in process requring students' email and password. Hence, the web has to 
protect students' data. 
2. Techology requirements. The creators of the web application Matrix will have to bring all the data like students' names and house from the old system to the new 
one. They also need to add the default input values for students to choose and refine the questions to make sure each one is necessary. Also, we users will need a 
training session to learn about how to use the new Matrix system.
3. System updating. As every year new students join and seniors leave, the database for the students' information has to be updated. Moreover, most of the 
students' house will change every year so the new system needs to update its database much more frequently than the old one.

### 3. What would be the advantages and limitations of hosting the Matrix on a local computer versus on the cloud?
Matrix on a local computer allows the users to freely access the web anytime they want with a faster speed as the web running program is stored in the local 
computer. Also, it usually can work offline so even if users forget to sign out on campus, they can still sign out where there's no networks. The limitation of 
this is that the users and mainly creators have to take care of the web such as by keeping the RAM upgrade as there maybe secure issues. Or even we need to pay at 
a very high cost for the web server upgrading and web maintainance. Also, people can only access to the web when the web is installed in the local computer.

Matrix on the cloud charges users lower cost in the long run because it includes backups, keeping the power going when there is an outage, applying security 
updates, and even replacing faulty hardware, which also means the data could be more secure and efficient. Using a cloud model can also allow you to access the web 
by typing the domain from any computer with internet. However, the cloud service has some restrictions for the users to access the web and causes the issues while 
moving larger files because it might take minutes to slow down the process.

### 4. Describe how would a Direct changeover, Parallel run, an ad phased implementation look like for the Matrix system? 
+ **Direct Changeover(Big bang adoption)** 

Every student and faculty would be asked to use the new Matrix system and discard the old one on a certain day. This would be too risky since the creators don't know what users 
think about the new system. If the new system is worse than the old one and users woould like to continue using the old but all the data in the old one was 
eliminated, then it was a serious data loss and user loss. 

+ **Parallel run**

Students and faculty would be informed that there is a new Matrix system in use and they can use both of the systems simultaneously. If the new Matrix system is 
worse than the old one, this time users have the old one to go back. When the new system is improved better and convinced by users during use, the old Matrix can 
be shut down completely.

+ **Ad phased implementation**

Similar to the parallel run, the old Matrix system will be kept while the new Matrix system is funcioning but gradually the data stored in the old system would be 
transferred to the new system. As time passed by, the users would depend on the new web more and more because it has a more completed database. Then eventually 
after the data finished transferring and users already get used to the new system, the old Matrix system will be completely replaced by the new Matrix system. 


### 5. What would be the consequences of a deficient transition from the old Google Form system to the Matrix, and to the New Matrix Reloaded? What would be the consequences of data loss?
Consequences of a deficient transition:  User loss and data loss because this terrible transition will lose the trust of the users.
Consequences of data loss: Users' personal information like the accounts will be lost.

### 6.[HL]
### 📔A book shop has a computer at each point of sale, and also a central computer. When a customer buys a book in the book shop, the salesperson at the point of sale uses a scanning device to input a barcode from the book. The barcode is sent to the central computer where the barcode of each book and the corresponding price are held in a database on a disk. When the price is found, it is sent to the point of sale computer where all necessary calculations are performed, details of the transaction are stored on a local disk and a receipt is printed out.

### a) Construct a system flow chart for the system described above.

<img src= "https://github.com/cathymonkey/Unit2/blob/main/SystemFlowChart.png" width = "800" height = "300">

### At the point of sale there are peripheral devices other than the scanning device and printer.

### b) Define peripheral devices
A Peripheral device is generally defined as any auxiliary device that connects to and works with the computer in some ways. There are three types of peripherals:
+ Input, used to interact with, or send data to the computer (mouse, keyboards, etc.)
+ Output, which provides output to the user from the computer (monitors, printers, etc.)
+ Storage, which stores data processed by the computer (hard drives, flash drives, etc.)

### c)Outline the purpose of one other possible peripheral device in this scenario.
A mouse and a keyboard connected with the sale computer for the staff to use the computer.

### The customers can also buy books online. A customer can select a book, and then enter their name, address and credit card number. This data is stored on the book shop’s central computer in a database of customer orders.

### d) Identify two sources of risk to personal data in this online system.
1. Data permanent loss due to no back-up system. In this online system, all the data is stored in a disk of the central computer, thus if the central computer is 
hacked or broken, the data in it couldn't be found back any more. 
2. Since the information of book price is related to the barcode of the book, if the barcode is destroyed or the barcode scanner is broken, then you can't find the book in the database and then no price.

### e) State two measures that the book shop can take to address the risks identified in part (d).
Measure 1: Establish a back-up system. It could be a hard drive or stored in the cloud.

Measure 2: Add a function that you can find the book price by the name or the author of the book in the database.

### f) Outline the consequences to the customer if their data is not adequately protected.
Since the local disk of the sale computer is used to record customers' transaction details, if this kind of data is stolen, then the customers' credit card 
accounts or their other payment app accounts as well as passwords would be exposed to the intruders. This will have a negative impact on customers' finance. Also, 
if the data of the book database has been tampered, this will cause financial and operational problems in the bookstore.    




