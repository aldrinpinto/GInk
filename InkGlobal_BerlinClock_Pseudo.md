Ink Global
====

<b>Current Role</b>: QA Manager

<b>Problem description</b>: https://bitbucket.org/inkmobile/berlin-clock/overview


<b>Solution Description</b>:

1.Divide the Value entered into hours, minutes, 

2.Seconds: Divide by 2 and if even then set to Yellow else Off

3.Hours: Here there are 2 segments --- First 4 lights and last 4 lights

  For the first 4 lights --Devide the hours by 5 to get quotient and set those lights as Red and leave remaining off
  
  ie.. if hour is 14 then 14/5 = 2 so first 2 lights will be Red so RROO
  
  For the second 4 lights--Divice the hours by 5 and get the remainder and set those lights as Red and leave remaining off
  
  ie..if hour is 14 then 14%5=4 so set 4 lights as Red - RRRR
  
  SO hours for 14 wil be RROO 
  
4.Minutes: Here there are 2 segments - First 11 lights and last 4 lights

  For the first 11 lights --Divide the Minutes by 5 to be quotient and also check if the quotient is divisible by 3. If divisble by 3 set that light as R and set the other light as per quotient as Yellow and rest are left off
  
  ie.. if Minutes is 16 then 16/5=3 and 3%3=0 so YYROOOOOOOO
  
  For the Minutes 4 lights-- Divide the Minutes by 5 and get remainder and set those lights as Yellow and leave remaining off
  
  ie.. if Minutes is 16 then 16%5=1 so set lights as Yellow - YOOOO
  
  So minutes for 16 will be YYROOOOOOOO YOOOO

6 Concat seconds, hours and minutes

 

<b>Pseudocode</b>:

1.Enter Time as a Input value in hh:mm:ss format - var hh = hour; var mm = minute; var ss = second

2.Check if the format is correct Ie.. hh is between 0 and 23;mm between 0 and 59; ss between 0 and 59

3.If format not valid --Display an error message and ask user to reenter

4.Else if format valid continue;

5.Calculate seconds String - 'SecStr'

  5a.Calculate a=Mod(ss,2)
  
     5a.1 if a =0 then secstr=Y
     
          else secstr=O
          
  5b. Berlinsec = secstr
          
6.Calculate Hours 

  Hrstr1[4]=[O,O,O,O];Hrstr2[4]=[O,O,O,O];
  
  6a.Caculate b=Div(hh,5)
  
     6a.1 for i = 0 to b-1
     
          set Hrstr1[i]=R
          
  6b. Calculate c=Mod(hh,5)
  
      6b.1 for i=0 to c-1
      
           set set Hrstr2[i]=R
           
  6c. Berlinhr = Concat(Hrstr1,' ',Hrstr2);
  
7.Calculate Minutes 

  Minstr1[11]=[O,O,O,O,O,O,O,O,O,O,O];Minstr2[4]=[O,O,O,O];
  
  6a.Caculate d=Div(mm,5)
  
     6a.1 for i = 0 to d-1
     
          if(mod(i+1,3)=0) then set Minstr1[i]=R
          
          else set Minstr1[i]=Y
          
  6b. Calculate e=Mod(mm,5)
  
      6b.1 for i=0 to e-1
      
           set set Minstr2[i]=Y
           
  6c. Berlinmin = Concat(Minstr1,' ',Minstr2)

8 output("Brelin click value is ",concat(Berlinsec,Berlinhr,Berlinmin));
           
           
<b>QA Scenarios</b>

1)Incorrect and correct time entry pushing the boundry cases for hour/minute/seconds

2)Extreme hour cases 00:00:00/23:59:59/24:00:00

3)Seconds:Positive cases where seconds is even and then when seconds is odd

4)Hours:Hour can be 0 or divisible by 5(10) or not fully divisble by 5(16)

5)Minutes: Min can be fully divisble by 5 and also fuly divisble by 3(30) or Min can be fully divisble by 5 and not fully divisble by 3(20)

Min Can be not fully divisble by 5 but fully divisible by 3 (9) or Min can be not fully dvisble by 5 and 3 (17)

Thanks
Aldrin

          
          
          


