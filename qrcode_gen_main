"""#-------------2d barcode----------------------------------
from pdf417gen import encode, render_image, render_svg
import _io
import pyqrcode
import PIL
from PIL import Image
# Some data to encode
name = "Name: Balaaji~"
age = "\nAge: 25~"
gender = "\nGender: Male~"
allergen = "\nAllergen: peanut~"
Diagnosis = "\nDiagnosis: ViralFever~"
Hypertensive = "\nHypertensive: No~"

value = name+age+gender+allergen+Diagnosis+Hypertensive
print("splitval: ",value.split("~"))

#myval = str([])
#print(value.splitlines(3))
#myval = value.splitlines(3)
#print("myval:",myval)


# Convert to code words
codes = encode(value)"""

# Generate barcode as image
#image = render_image(codes)  # Pillow Image object
#image.save('longestword.jpg')

# Generate barcode as SVG
#svg = render_svg(codes)  # ElementTree object
#svg.write("longestword.svg")

#qrcode_file = open(r"C:\Users\Trainee\Desktop\longestword.jpg","rb+")
#qrcode_file.close()
#val = _io.BufferedRandom.read(qrcode_file)
#bytearray.decode(val)
#print(bytearray.fromhex(str(val)).decode("bytes"))
#file = open(r"C:\Users\Trainee\Desktop\barcodefile.txt","a+")
#file.writelines(str(val))

#file.close()


#-------2d barcode_qr_code----------------------------------------

#imageobject = pyqrcode.create(value)

#imageobject.png('qrcode.png',scale=5)
#imageobject.svg('qrcode.svg',scale=5) 

#-------------------------------instructions------------------------------------
#Versions 1 through 9
#Numeric mode: 10 bits
#Alphanumeric mode: 9 bits
#Byte mode: 8 bits
#Japanese mode: 8 bits

String = "QR SAMPLE";
NumericMode = '0001';
AlphaNumericMode = '0010';
ByteMode = '0100';
charactercount = bin(len(String))
n = 8;
num_value = 0;
#---------creating the code for enocding mode and character count--------------- 
if (len(String) < 16) & (type(String) == str):
    ModeSelector = AlphaNumericMode

charactercount = charactercount.strip('0b')
charactercount = charactercount.rjust(9,'0')
print(ModeSelector+charactercount.rjust(9,'0'))
#---------------encoding the data in Alphanumeric mode--------------------------
strarray = list()
for i,k in enumerate(String):
    k = int(ord(k))
    print(i,k)
    if (i%2 == 0):
        k = k*45
        print(k)
    strarray.append(k)
    if (i>0) or (i == i+1):
        strarray[i-1] = k+strarray[i-1]

print(strarray)
print(strarray[-1]//45 )
strarray[-1] = strarray[-1]//45 
for i,k in enumerate(strarray):
    k = bin(k)
    print("---> ",k)
    k = k.strip('0b')
    if (i%2 == 0):
        k = k.rjust(6,'0')
        if i != len(strarray)-1:
            k = k.rjust(2,'0')
        strarray[i] = k

print(strarray)
for i,k in enumerate(strarray):
    print(i)
    if i<len(strarray)-1:
        strarray.pop(i+1)
strarray.insert(0,charactercount)
strarray.insert(0,ModeSelector)

print(strarray)
for i,k in enumerate(strarray):
    if i<len(strarray)-1:
        strarray[i+1] = strarray[i] + strarray[i+1]
print("-----")
print(strarray)
strarray_val = strarray[-1]
#----------------------add padding terminator bits for encoding-----------------
ver_1_encode_bits = 104
ver_1_tobeencoded = len(strarray_val)

if (ver_1_encode_bits-4)>ver_1_tobeencoded:
    strarray_val = strarray_val+'0000'
    print("val",strarray_val)

if (len(strarray_val)%8)!=0:
    while(1):
        if len(strarray_val)%8 == 0:
            break
        strarray_val = strarray_val+'0'
        pass
print("values:",strarray_val)


#-------------------Adding pad bytes to fit the full capacity-------------------
if len(strarray_val)<104:
    while(1):
        if len(strarray_val) == 104:
            break
        strarray_val = strarray_val+'11101100'
        if len(strarray_val) < 104:
            strarray_val = strarray_val+'00010001'
        pass

print("myval",strarray_val)

#for i in strarray[0:len(strarray):2]:
Stripped_value = [strarray_val[i:i+n] for i in range(0,len(strarray_val),n)]
print("strippedvalue:",Stripped_value)

value = 0
for i,k in enumerate(Stripped_value[1]):
    value = value*2+int(k)
    refval = bin(value)
    refval = refval.strip('0b')
    print("step:",refval)
    if len(refval)==len(Stripped_value[i]):
        if value>256:
            xored_value =  value^285
            value = xored_value
            pass
        else:
            print("==")
print(value)
#Stripped_value1 = Stripped_value
#binarycollection = list()
#print(Stripped_value1)
#for i in Stripped_value1[0:len(Stripped_value1):1]:
#    i.split(' ')

#    if i.isspace == True:
#        print(i.split(' '))
    
#for i in Stripped_value1[0:len(Stripped_value1):1]:
#    split_value = i.split(' ')
#    for j in split_value[0:len(split_value):1]:
#        if j.isalpha == True:
#            if j.index == 0:
#                num_value = int(ascii(j))*45
#            if j.index == 1:
#                num_value = num_value + int(ascii(j))
#        elif j.isspace == True:
#indexval = int(i.index)
#            split_value[i] = int(ascii(j))
#            bin_value = split_value.rjust(6,'0')
#        else:
            
#     print(split_value)
