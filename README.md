# سنقوم ببرنامج بلغة بايثون يستطيع فيه المستخدم تحديد موعد اخذ علاجه على الحاسب وعندما يحين وقت الدواء سيقوم البرنامج بارسال رساله صوتيه على الحاسب وايضا سيقوم بأرسل رساله نصيه على هاتف المريض لتذكيره بعلاجه وايضا يقوم بالاتصال على هاتف المريض لتذكيره بموعد علاجه 
المتدرب:اسامه العتيبي
المتدرب:مشعل العصيل 
المتذرب سعود المري 



import datetime
import pyttsx3
from twilio.rest import Client


account_sid = 'ACe75630e459eeb5d8c679b5f1c92a2cf2'
auth_token = 'e5a5d2a1bf85ce62a9bc8a6daf4ac5fd'
twilio_phone_number = '+17622167118'
your_phone_number = '+966590121884'

engine = pyttsx3.init()

medicine_time = datetime.datetime.now().replace(hour=4, minute=51, second=0, microsecond=0)


if datetime.datetime.now() >= medicine_time:
    engine.say("حان وقت الدواء")
    engine.runAndWait()



    client = Client(account_sid,auth_token)
    message = client.messages.create(
       body="حان وقت تناول الدواء ",
       from_= twilio_phone_number, 
       to = your_phone_number
    )

    print("تم ارسال الرساله بنجاح")
else:
    print("لم يحن الوقت للدواء")
