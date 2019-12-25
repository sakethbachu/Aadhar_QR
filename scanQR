# import the necessary packages
from pyzbar import pyzbar
import argparse
import cv2

#initializing all the variables once for all
a=b=c=d=e=f=i=0
#initializing empthy strings
abc = ''

# construct the argument parser and parse the arguments
ap = argparse.ArgumentParser()
ap.add_argument("-i", "--image", required=True,
	help="path to input image")
args = vars(ap.parse_args())

# load the input image
image = cv2.imread(args["image"])

# find the barcodes in the image and decode each of the barcodes
barcodes = pyzbar.decode(image)

# loop over the detected barcodes
for barcode in barcodes:
	# extract the bounding box location of the barcode and draw the
	# bounding box surrounding the barcode on the image
	(x, y, w, h) = barcode.rect
	cv2.rectangle(image, (x, y), (x + w, y + h), (0, 0, 255), 2)

	# the barcode data is a bytes object so if we want to draw it on
	# our output image we need to convert it to a string first
	barcodeData = barcode.data.decode("utf-8")
	barcodeType = barcode.type

	# draw the barcode data and barcode type on the image
	text = "{} ({})".format(barcodeData, barcodeType)
	cv2.putText(image, text, (x, y - 10), cv2.FONT_HERSHEY_SIMPLEX,
		0.5, (0, 0, 255), 2)
    
for c in range(e, len(barcodeData)):
    i=f= 0
    for b in range(e, len(barcodeData)):
        if b < len(barcodeData)-1:
            
            if barcodeData[b+1] == '=':
                i=i+1
                f=i
                break;
        
            if barcodeData[b+1] == '"':
                abc = abc+' '
                i=i+1
                f=i
                break;
            
            
            if barcodeData[b+1] != '=' or barcodeData[b+1] != '"':
             
                 abc=abc+barcodeData[b+1]
                 i=i+1
                 f=i
    
    
    e=e+f
        
#function to replace certain substrings of the barcodeData string
replace_list = ['<PrintLetterBarcodeData', '/>']
def remove_multiple_strings(cur_string, replace_list):
  for cur_word in replace_list:
    cur_string = cur_string.replace(cur_word, '')
  return cur_string

#a function to take newline in an existing string 
def take_newline(a):
    i=e=0
    cdf = ' '
    for i in range(e, len(a)):
        if a[i] == '' or a[i] == ' ':
            cdf = cdf + '\n'
        else:
            cdf = cdf+a[i]
    return(cdf)    

#doing changes to the string
abc=remove_multiple_strings(abc, replace_list)  
#now we can compare the contents of the string 'v' with the result coming from ocr
v = take_newline(abc)    

# show the output image
cv2.imshow("Image", image)
cv2.waitKey(0)
