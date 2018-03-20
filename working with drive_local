
#
# These codes are meant to be run from Jupyter Noteboos only
#

import pandas as pd
from io import BytesIO

#Authenticating with Goolge. This will open a popup for you to add key
from google.colab import auth
auth.authenticate_user()

from googleapiclient.discovery import build
drive_service = build('drive', 'v3')


import io
from googleapiclient.http import MediaIoBaseDownload


#################
# file in google drive

#This file id is the last tag when you create create shareable link for your file
file_id = ''


request = drive_service.files().get_media(fileId=file_id)
downloaded = io.BytesIO()
downloader = MediaIoBaseDownload(downloaded, request)
done = False
while done is False:
  # _ is a placeholder for a progress object that we ignore.
  # (Our file is small, so we skip reporting progress.)
  _, done = downloader.next_chunk()

downloaded.seek(0)
# print('{}'.format(downloaded.read()))


stores = pd.read_csv(downloaded, encoding='utf8', sep=",")
####################

#################
# file in local - this will prompt you to browse for your local file

from google.colab import files

uploaded = files.upload()

for fn in uploaded.keys():
  print('User uploaded file "{name}" with length {length} bytes'.format(
      name=fn, length=len(uploaded[fn])))
      
 #uploaded is a dictionary with data accessible by key(filename)
from io import BytesIO

import pandas as pd


df = pd.read_csv(BytesIO(uploaded["filename.csv"]), encoding='utf8', sep=",")

####################
