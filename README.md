
Open In Colab
In [0]:
#@markdown <h3>⬅ Run This Cell to  Mount Gdrive
from google.colab import drive
drive.mount('/content/drive')
RcloneLab¶
In [0]:
#@markdown <h3>⬅️ Run This Cell to Install Skillshare-DL Requirements</h3>
import random, string, urllib.request, json, getpass, os, IPython, uuid
import ipywidgets as widgets

from IPython.display import HTML, clear_output

loadingBtn = widgets.Button(description = "Installing",
                          disabled = True,
                          button_style = 'warning', # 'success', 'info', 'warning', 'danger' or '' 
                          tooltip = "Installing",
                          icon = 'check')
display(loadingBtn)

if not os.path.exists("/opt/python3.7"):
  get_ipython().system_raw("rm -rf /content/sample_data/ && sudo apt update && sudo apt install software-properties-common")
  get_ipython().system_raw("sudo add-apt-repository ppa:deadsnakes/ppa")
  get_ipython().system_raw("sudo apt install python3.7")
  get_ipython().system_raw("sudo apt install python3-pip")
  get_ipython().system_raw("python3.7 -m pip install --upgrade pip setuptools wheel")
  get_ipython().system_raw("git clone https://github.com/calvinhobbes23/Skillshare-DL.git /root/.Skillshare-DL")
  get_ipython().system_raw("rm -r /root/.Skillshare-DL/Skillshare_DL_[KENWAY].ipynb")
  clear_output()

try:
  get_ipython().system_raw("python3.7 -m pip -q install -r /root/.Skillshare-DL/requirements.txt")
  display(HTML("<center><h2 style=\"font-family:Trebuchet MS;color:#4f8bd6;\">Successfully Configured!</h2><br></center>"))
  
except:
  display(HTML("<center><h2 style=\"font-family:Trebuchet MS;color:#ff0000;\">Error Occured, Rerun the Cell!!</h2><br></center>"))
In [0]:
#@markdown <h3>⬅️ Run this Cell to Download Skillshare Course</h3>
Course_Link = "" #@param {type:"string"}
!python3.7 /root/.Skillshare-DL/dl.py "$Course_Link"
In [0]:
#@markdown <h3>⬅️ Run This Cell to  Move Downloaded Courses to Gdrive
!mv /content/Skillshare "/content/drive/My Drive/Skillshare-DL"
