# Sending-SMS-with-Python
Sample code for sending SMS in Python code
import urllib3


USER_NUMBER = "09333739999"
USER_KEY = "usb42qe7g2n8r"
MSG_TO_SEND = input('این پیامک تبلیغاتی مریم کارآموز برنامه نویسی پایتون می باشد ')

http = urllib3.PoolManager()
url = "https://smsapi.free-mobile.fr/sendmsg?user={user}&pass={passw}&msg={msg}".format(user = USER_NUMBER, passw = USER_KEY, msg = MSG_TO_SEND)

r = http.request('POST', url)
r.status = int(r.status)


if r.status == 200:
  """The SMS has been sent to your mobile successfully."""
  print("The SMS has been sent to your mobile successfully.")

elif r.status == 400:
  """One of the mandatory parameters is missing."""
  print("One of the parameters is missing.")

elif r.status == 402:
  """Too many SMS were sent in too little time."""
  print("Too many SMS were sent in too little time.")

elif r.status == 403:
  """SMS Api is not activated on the subscriber space, or login/password isn't correct."""
  print("SMS API is not activated on the subscriber space, or login/password isn't correct.")

elif r.status == 500:
  """Servor-side error, please try again later."""
  print("Servor-side error, please try again later.")

else:
  """Unknown error"""
  print("Unknown error")

exit()
