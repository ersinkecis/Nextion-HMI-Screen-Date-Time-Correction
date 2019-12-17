# Nextion-HMI-Screen-Date-Time-Correction
Nextion HMI Screen Date-Time Correction

//this code must be in btnSet button in Nextion HMI IDE.<br>
//Objects that should be in the screen design:<br>
//"numDay, numMonth, numYear, numHour, numMinute, numSecond" are Number.<br>
//txtInfo is Text.<br>
//btnSet is Button.<br>
//varMod is numeric variable.<br>
<br>
rtc0=numYear.val //year<br>
rtc1=numMonth.val //month<br>
rtc2=numDay.val //day<br>
rtc3=numHour.val //hour<br>
rtc4=numMinute.val //minute<br>
rtc5=numSecond.val //second<br>
txtInfo.txt="" //day of week OR error information.<br>
<br>
//developer: Ersin Kecis - ersinkecis@gmail.com<br>
//date time: 16.12.2019 23:50<br>
//date-time validation code start here:<br>
if(numYear.val<0)<br>
{<br>
  txtInfo.txt="You have entered an incorrect YEAR."<br>
}else if(numMonth.val<0||numMonth.val>12)<br>
{<br>
  txtInfo.txt="You have entered an incorrect MONTH."<br>
}else if(numMonth.val==2)<br>
{<br>
  varMod.val=numYear.val //2019<br>
  varMod.val%=4 //2019 mod 4 >--> equal >--> 3<br>
  if(varMod.val==0)<br>
  {<br>
    if(numDay.val>29||numDay.val<0)<br>
    {<br>
      txtInfo.txt="You have entered an incorrect DAY."<br>
    }<br>
  }else<br>
  {<br>
    if(numDay.val>28||numDay.val<0)<br>
    {<br>
      txtInfo.txt="You have entered an incorrect DAY."<br>
    }<br>
  }<br>
}else if(numMonth.val==1||numMonth.val==3||numMonth.val==5||numMonth.val==7||numMonth.val==8||numMonth.val==10||numMonth.val==12)<br>
{<br>
  if(numDay.val>31||numDay.val<0)<br>
  {<br>
    txtInfo.txt="You have entered an incorrect DAY."<br>
  }<br>
}else if(numDay.val>30||numDay.val<0)<br>
{<br>
  txtInfo.txt="You have entered an incorrect DAY."<br>
}<br>
if(txtInfo.txt=="")<br>
{<br>
  if(rtc6==0)<br>
  {<br>
    txtInfo.txt="Sunday"<br>
  }else if(rtc6==1)<br>
  {<br>
    txtInfo.txt="Monday"<br>
  }else if(rtc6==2)<br>
  {<br>
    txtInfo.txt="Tuesday"<br>
  }else if(rtc6==3)<br>
  {<br>
    txtInfo.txt="Wednesday"<br>
  }else if(rtc6==4)<br>
  {<br>
    txtInfo.txt="Thursday"<br>
  }else if(rtc6==5)<br>
  {<br>
    txtInfo.txt="Friday"<br>
  }else if(rtc6==6)<br>
  {<br>
    txtInfo.txt="Saturday"<br>
  }else<br>
  {<br>
    txtInfo.txt="-"<br>
  }<br>
}<br>
