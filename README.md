# Nextion-HMI-Screen-Date-Time-Correction
Nextion HMI Screen Date-Time Correction

//this code must be in btnSet button in Nextion HMI IDE.
//Objects that should be in the screen design:
//"numDay, numMonth, numYear, numHour, numMinute, numSecond" are Number.
//txtInfo is Text.
//btnSet is Button.
//varMod is numeric variable.

rtc0=numYear.val //year
rtc1=numMonth.val //month
rtc2=numDay.val //day
rtc3=numHour.val //hour
rtc4=numMinute.val //minute
rtc5=numSecond.val //second
txtInfo.txt="" //day of week OR error information.

//developer: Ersin Kecis - ersinkecis@gmail.com
//date time: 16.12.2019 23:50
//date-time validation code start here:
if(numYear.val<0)
{
  txtInfo.txt="You have entered an incorrect YEAR."
}else if(numMonth.val<0||numMonth.val>12)
{
  txtInfo.txt="You have entered an incorrect MONTH."
}else if(numMonth.val==2)
{
  varMod.val=numYear.val //2019
  varMod.val%=4 //2019 mod 4 >--> equal >--> 3
  if(varMod.val==0)
  {
    if(numDay.val>29||numDay.val<0)
    {
      txtInfo.txt="You have entered an incorrect DAY."
    }
  }else
  {
    if(numDay.val>28||numDay.val<0)
    {
      txtInfo.txt="You have entered an incorrect DAY."
    }
  }
}else if(numMonth.val==1||numMonth.val==3||numMonth.val==5||numMonth.val==7||numMonth.val==8||numMonth.val==10||numMonth.val==12)
{
  if(numDay.val>31||numDay.val<0)
  {
    txtInfo.txt="You have entered an incorrect DAY."
  }
}else if(numDay.val>30||numDay.val<0)
{
  txtInfo.txt="You have entered an incorrect DAY."
}
if(txtInfo.txt=="")
{
  if(rtc6==0)
  {
    txtInfo.txt="Sunday"
  }else if(rtc6==1)
  {
    txtInfo.txt="Monday"
  }else if(rtc6==2)
  {
    txtInfo.txt="Tuesday"
  }else if(rtc6==3)
  {
    txtInfo.txt="Wednesday"
  }else if(rtc6==4)
  {
    txtInfo.txt="Thursday"
  }else if(rtc6==5)
  {
    txtInfo.txt="Friday"
  }else if(rtc6==6)
  {
    txtInfo.txt="Saturday"
  }else
  {
    txtInfo.txt="-"
  }
}
