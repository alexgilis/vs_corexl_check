# vs_corexl_check

What is it?
------------
This BASH script is to be run on Check Point VSX appliances in order to provide a quick overview of the CoreXL distribution of each VS and the total instances in use.

How do I install it?
--------------------
Copy the content of the script on your system and make it executable with chmod +x.

How does it work?
-----------------
The script will use the output of "vsx stat -v" and will parse it with awk in order to detect VSID and names.
Once this is done, it will parse through the VS and use cpwd_admin for the VSID in order to read the line detailing the number of instances.
There is some logic to detect if VSID are not contiguous. It can happen if you had virtual systems deleted and other added afterwards.
Finally, the script will give you the total amout of instances in use in your system.

Can I run it any time?
----------------------
Normally yes, but as always with production environments, take caution when running custom scripts.
The script will create variables for data maniulation which shoudln't interfere with regular VSX operations.
Try it first on your standby member or outside of peak hours.
The script does not write anything and does not call any other command than "vsx stat -v".
As of today there are no yet VSX API that can be used for that kind of checks.

DISCLAIMER
----------
vs_corexl_check is provided as is and is not supported or endorsed by Check Point.
The author of the script can not be held liable for any damage, loss of information, system malfunction be it hardware or software, negative business impact, loss of revenue and any other consequences resulting from the use of the script.
The author of the script is not obligated to provide any assistance or updates to users of this script.
By using the script, you agree on the provisions of this disclaimer.
