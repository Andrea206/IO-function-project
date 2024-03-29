#  File I/O Lambda Function:
Creates, deletes, updates a large number of files.
<br/>

###### written by [Ailian Li](https://github.com/ailian16) 
###### Cloud Computing Research at University of Washington - Tacoma, lead by [Dr. Wes Lloyd](https://github.com/wlloyduw)
<br/>

##  I/O arguments
**“numfiles”**	# of Files Parameter

**“fileop”** 	Type of operations parameter: SR-sequential-read, RR-random-read, TR- Static Read,  W-write
		
**“numfileops”**	Number of ops to perform against a file.  An op is reading or writing a byte or line to a file

 **“optype”**	L-read/write lines (random 80-char ASCII string), B-read/write bytes

**“nodelete”**	true/false - indicates whether files created should be deleted at the end of the Lambda function

**Input JSON**
```javascript
         		{
	"numfiles": 100,
	"fileops": "SR",
	“numfileops”: 1000,
	“optype”: “L”,
	“nodelete”: true
}
```

<br/><br/>

# I/O function utilizes the faas_inspector:<br/><br/>


## faas_inspector

This project provides coding templates to support tracing FaaS function server infrastructure for code deployments.
A generic Hello World function is provided for different FaaS platform/language combinations as a starting point to write infrastructure traceable FaaS functions to enable tracing code containers and hosts (VMs) created by FaaS platform providers for hosting FaaS functions.  This information can help verify the state of infrastructure (COLD vs. WARM) to understand performance results, and help preserve infrastructure for better FaaS performance.

__**Example Input/Output:**__

**Input JSON**
```javascript
{
	"Name": "Fred Smith"
}
```

**Output JSON**
```javascript
{
	"value": "Hello Fred Smith",
	"uuid": "cec76fba-9695-4f93-b906-f6eef96543bd",
	"vmuptime": 1539908883,
	"newcontainer": 1
}
```
| **Field** | **Description** |
| --------- | --------------- |
| uuid | the uniquely identifies each container created by AWS |
| vmuptime | provides a unique way to identify the host.  Requires no two hosts to have exactly the same boot time to the nearest second.  In theory it is possible that two VMs could boot at the same time, but it is very rare in the scope of hosting a single Lambda function. |
| newcontainer | 0-indicates the container has been recycled, 1-indicates the container is new |

**Platforms/Languages Supported:**

| **Platform/Language** | **Description** |
| --------------------- | --------------- |
| lambda/java_template | skeleton hello function for AWS Lambda/Java provided as a mvn project |
