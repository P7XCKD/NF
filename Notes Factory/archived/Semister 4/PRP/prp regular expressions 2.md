```python
import re
data = ''' Hello, this is a regex test! Contact me at john.doe@example.com or admin@test.org. 
Call me at 9876543210 or (123) 456-7890. Event on 12/03/2024 and 03-12-2023 at 10:30 AM. 
Follow @john_doe and use #coding. Price is $99.99, ₹500, and €20. 
Server IPs: 192.168.1.1, 10.0.0.1. Visit https://example.com or www.test.org.
My Aadhaar: 1234 5678 9012, and ZIP codes are 12345, 98765. 
Vehicle: MH 12 AB 1234, Card: 1234-5678-9012-3456, Exp: 12/24.
Stock prices: AAPL is up, TSLA is down. Colors: #FF5733, #abcdef.
Python function: def my_function(param): return param. 
YouTube link: https://www.youtube.com/watch?v=dQw4w9WgXcQ.
ISBN: 978-3-16-148410-0, MAC: AA:BB:CC:11:22:33. 
I love Python, JavaScript, and C++. My password: Passw0rd!123'''
''



# 1️⃣ Extract all words from the text (ignore punctuation).

words = re.findall('[a-zA-Z]', data)

print("Words found:")

well = ''.join(words)

print(" text : ", well)


# 2️⃣ Extract all numbers
numbers = re.findall('\d', data)
well = ''.join(numbers)

print("\nnumbers :" ,well)

# 3️⃣ Extract all email addresses
pass

# 4️⃣ Extract all phone numbers
phone_numbers = re.findall('(\d{10}|\(\d{3}\)\s\d{3}-\d{4})', data)

print("\nphone numbers: ", phone_numbers)

# 5️⃣ Extract all dates
dates = re.findall(r'(\d{2}[/\-]\d{2}[/\-]\d{4})', data)

print("\ndates: ", dates)


# 6️⃣ Extract all time values
times = re.findall('\d{1,2}:\d{2}\s?(?:AM|PM)', data)
well = ''.join(times)
print("\ntimes: ", well)


# 7️⃣ Extract all hashtags
hashtags = re.findall('#\w+', data)

print("\nhashtags: ", hashtags)

# 8️⃣ Extract all Twitter-style mentions
mentions = re.findall('@\w+', data)

print("\nmentions: ", mentions)

# 9️⃣ Extract all currency values
currencies = re.findall('[$₹€]\d+(?:\.\d+)?', data)

print("\ncurrencies: ", currencies)

# 🔟 Extract all 5-digit ZIP codes
zip_codes = re.findall(r'\b\d{5}\b', data)

print("\nzip codes: ", zip_codes)


```

output:

 text :  HellothisisaregextestContactmeatjohndoeexamplecomoradmintestorgCallmeatorEventonandatAMFollowjohndoeandusecodingPriceisandServerIPsVisithttpsexamplecomorwwwtestorgMyAadhaarandZIPcodesareVehicleMHABCardExpStockpricesAAPLisupTSLAisdownColorsFFabcdefPythonfunctiondefmyfunctionparamreturnparamYouTubelinkhttpswwwyoutubecomwatchvdQwwWgXcQISBNMACAABBCCIlovePythonJavaScriptandCMypasswordPasswrd

numbers : 9876543210123456789012032024031220231030999950020192168111000112345678901212345987651212341234567890123456122457334997831614841001122330123

phone numbers:  ['9876543210', '(123) 456-7890']

dates:  ['12/03/2024', '03-12-2023']

times:  10:30 AM

hashtags:  ['#coding', '#FF5733', '#abcdef']

mentions:  ['@example', '@test', '@john_doe']

currencies:  ['$99.99', '₹500', '€20']

zip codes:  ['12345', '98765']