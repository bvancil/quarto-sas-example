# Example of using Quarto with SAS (via `sas_kernel`)

## Prerequisites

1. Install a Java Runtime Environment (required by `sas_kernel`), and add it to your system's `PATH` variable.
1. Put SAS's `SASHome\SASFoundation\9.4\core\sasext` in your system's `PATH` variable.
1. Install [Quarto](https://quarto.org/).
1. Use Python and Pipenv to install the packages listed in the included `Pipfile`. Usually `pipenv install --dev` should do the trick.
1. Check that `jupyter kernelspec list` lists the "sas" kernel.
1. For an operating system other than Windows, edit `sascfg_personal.py` to select your SAS configuration.

## Building the Quarto output

From shell prompt:

1. `pipenv shell`
1. `quarto render sas-example.qmd`

## Troubleshooting

### Verify that Jupyter is set up correctly

1. `jupyter nbconvert check-python.ipynb --to html --execute`
1. `quarto check jupyter`

### Check that quarto and python work with the pure Python version

1. `quarto render check-python.qmd --debug`

### Try the saspy version

1. `quarto render check-saspy.qmd --debug`

### Keep intermediate artifacts

1. `quarto render sas-example.qmd --debug`

### Render in stages

1. `quarto convert sas-example.qmd`
1. Inspect `sas-example.ipynb`.
1. `quarto render sas-example.ipynb`

## TODO

```
C:\Users\bvancil\scoop\apps\openjdk\current\bin\java.EXE -classpath "C:\Users\bvancil\.virtualenvs\quarto-sas-example-Ugam9axL\lib\site-packages\saspy\java\saspyiom.jar;C:\Users\bvancil\.virtualenvs\quarto-sas-example-Ugam9axL\lib\site-packages\saspy\java\iomclient\log4j-1.2-api-2.12.4.jar;C:\Users\bvancil\.virtualenvs\quarto-sas-example-Ugam9axL\lib\site-packages\saspy\java\iomclient\log4j-api-2.12.4.jar;C:\Users\bvancil\.virtualenvs\quarto-sas-example-Ugam9axL\lib\site-packages\saspy\java\iomclient\log4j-core-2.12.4.jar;C:\Users\bvancil\.virtualenvs\quarto-sas-example-Ugam9axL\lib\site-packages\saspy\java\iomclient\sas.security.sspi.jar;C:\Users\bvancil\.virtualenvs\quarto-sas-example-Ugam9axL\lib\site-packages\saspy\java\iomclient\sas.core.jar;C:\Users\bvancil\.virtualenvs\quarto-sas-example-Ugam9axL\lib\site-packages\saspy\java\iomclient\sas.svc.connection.jar;C:\Users\bvancil\.virtualenvs\quarto-sas-example-Ugam9axL\lib\site-packages\saspy\java\iomclient\sas.rutil.jar;C:\Users\bvancil\.virtualenvs\quarto-sas-example-Ugam9axL\lib\site-packages\saspy\java\iomclient\sas.rutil.nls.jar;C:\Users\bvancil\.virtualenvs\quarto-sas-example-Ugam9axL\lib\site-packages\saspy\java\iomclient\sastpj.rutil.jar;C:\Users\bvancil\.virtualenvs\quarto-sas-example-Ugam9axL\lib\site-packages\saspy\java\thirdparty\glassfish-corba-internal-api.jar;C:\Users\bvancil\.virtualenvs\quarto-sas-example-Ugam9axL\lib\site-packages\saspy\java\thirdparty\glassfish-corba-omgapi.jar;C:\Users\bvancil\.virtualenvs\quarto-sas-example-Ugam9axL\lib\site-packages\saspy\java\thirdparty\glassfish-corba-orb.jar;C:\Users\bvancil\.virtualenvs\quarto-sas-example-Ugam9axL\lib\site-packages\saspy\java\thirdparty\pfl-basic.jar;C:\Users\bvancil\.virtualenvs\quarto-sas-example-Ugam9axL\lib\site-packages\saspy\java\thirdparty\pfl-tf.jar" pyiom.saspy2j -host localhost -stdinport 53718 -stdoutport 53719 -stderrport 53720 -zero -lrecl 1048576
ERROR StatusLogger No Log4j 2 configuration file found. Using default configuration (logging only errors to the console), or user programmatically provided configurations. Set system property 'log4j2.debug' to 
show Log4j 2 internal initialization logging. See https://logging.apache.org/log4j/2.x/manual/configuration.html for instructions on how to configure Log4j 2
We failed in getConnection
The native implementation module for the security package could not be found in the path.com.sas.services.connection.FatalConnectionFactoryException: The native implementation module for the security package could not be found in the path.
        at com.sas.services.connection.ClusterEnvelope.getConnection(ClusterEnvelope.java:248)
        at com.sas.services.connection.AggregationKernel.doGetConnection(AggregationKernel.java:242)
        at com.sas.services.connection.ConnectionFactoryKernel.getConnection(ConnectionFactoryKernel.java:325)
        at com.sas.services.connection.ConnectionFactoryShell.getConnection(ConnectionFactoryShell.java:69)
        at com.sas.services.connection.ConnectionFactoryShell.getConnection(ConnectionFactoryShell.java:51)
        at pyiom.saspy2j.main(saspy2j.java:201)
Caused by: org.omg.CORBA.INITIALIZE: The native implementation module for the security package could not be found in the path.  vmcid: 0x0  minor code: 0  completed: No
        at com.sas.iom.orb.brg.SecurityPackageBase.initClient(SecurityPackageBase.java:70)
        at com.sas.iom.orb.brg.Engine.createSecurityPackage(Engine.java:5530)
        at com.sas.iom.orb.brg.Engine.flowSendAuth(Engine.java:4312)
        at com.sas.iom.orb.brg.Engine.flow(Engine.java:717)
        at com.sas.iom.orb.brg.Engine.initClient(Engine.java:676)
        at com.sas.iom.orb.brg.ORBImpl.uri_to_object(ORBImpl.java:114)
        at com.sas.services.connection.ClusterEnvelope.createObject(ClusterEnvelope.java:394)
        at com.sas.services.connection.ClusterEnvelope.getConnection(ClusterEnvelope.java:86)
        ... 5 more
Caused by: java.lang.UnsatisfiedLinkError: no sspiauth in java.library.path: C:\Users\bvancil\scoop\apps\openjdk\current\bin;C:\WINDOWS\Sun\Java\bin;C:\WINDOWS\system32;C:\WINDOWS;C:\Users\bvancil\.virtualenvs\quarto-sas-example-Ugam9axL/Scripts;C:\Program Files\PowerShell\7;C:\Users\bvancil\bin;C:\Program Files\Git\mingw64\bin;C:\Program Files\Git\usr\local\bin;C:\Program Files\Git\usr\bin;C:\Program Files\Git\usr\bin;C:\Program Files\Git\mingw64\bin;C:\Program Files\Git\usr\bin;C:\Users\bvancil\bin;C:\Users\bvancil\scoop\apps\cmder\current\vendor\conemu-maximus5\ConEmu\Scripts;C:\Users\bvancil\scoop\apps\cmder\current\vendor\conemu-maximus5;C:\Users\bvancil\scoop\apps\cmder\current\vendor\conemu-maximus5\ConEmu;C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.2\bin;C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.2\libnvvp;C:\Oracle\product\19.0.0\client_1\bin;C:\WINDOWS\system32;C:\WINDOWS;C:\WINDOWS\System32\Wbem;C:\WINDOWS\System32\WindowsPowerShell\v1.0;C:\WINDOWS\System32\OpenSSH;C:\Program Files\SASHome\SASFoundation\9.4\core\sasexe;C:\Program Files\SASHome\SASFoundation\9.4\ets\sasexe;C:\Program Files\SASHome\Secure\ccme4;C:\Program Files\Git\cmd;C:\Program Files\NVIDIA Corporation\Nsight Compute 2020.3.1;C:\Program Files (x86)\NVIDIA Corporation\PhysX\Common;C:\Program Files\PowerShell\7;C:\Program Files (x86)\GnuPG\bin;C:\Users\bvancil\scoop\apps\vscode\current\bin;C:\Users\bvancil\scoop\apps\gpg4win\4.1.0\GnuPG\bin;C:\Users\bvancil\scoop\apps\gpg4win\4.1.0\Gpg4win\bin;C:\Users\bvancil\scoop\apps\pyenv\current\pyenv-win\bin;C:\Users\bvancil\scoop\apps\pyenv\current\pyenv-win\shims;C:\Users\bvancil\scoop\apps\openjdk\current\bin;C:\Users\bvancil\scoop\apps\miktex\current\texmfs\install\miktex\bin\x64;C:\Users\bvancil\scoop\apps\ghostscript\current\lib;C:\Users\bvancil\scoop\shims;C:\Users\bvancil\AppData\Local\Microsoft\WindowsApps;C:\users\bvancil\appdata\roaming\python\python311\scripts;C:\users\bvancil\.local\bin;C:\Program Files\Git\usr\bin\vendor_perl;C:\Program Files\Git\usr\bin\core_perl;.
        at java.base/java.lang.ClassLoader.loadLibrary(ClassLoader.java:2444)
        at java.base/java.lang.Runtime.loadLibrary0(Runtime.java:848)
        at java.base/java.lang.System.loadLibrary(System.java:2047)
        at com.sas.security.sspi.SSPIAuth.loadNativeLibrary(SSPIAuth.java:499)
        at com.sas.security.sspi.SSPIAuth.<init>(SSPIAuth.java:163)
        at com.sas.iom.orb.brg.SecurityPackageBase.initClient(SecurityPackageBase.java:62)
        ... 12 more
```

After fixing path

```
C:\Users\bvancil\scoop\apps\openjdk\current\bin\java.EXE -classpath "C:\Users\bvancil\.virtualenvs\quarto-sas-example-Ugam9axL\lib\site-packages\saspy\java\saspyiom.jar;C:\Users\bvancil\.virtualenvs\quarto-sas-example-Ugam9axL\lib\site-packages\saspy\java\iomclient\log4j-1.2-api-2.12.4.jar;C:\Users\bvancil\.virtualenvs\quarto-sas-example-Ugam9axL\lib\site-packages\saspy\java\iomclient\log4j-api-2.12.4.jar;C:\Users\bvancil\.virtualenvs\quarto-sas-example-Ugam9axL\lib\site-packages\saspy\java\iomclient\log4j-core-2.12.4.jar;C:\Users\bvancil\.virtualenvs\quarto-sas-example-Ugam9axL\lib\site-packages\saspy\java\iomclient\sas.security.sspi.jar;C:\Users\bvancil\.virtualenvs\quarto-sas-example-Ugam9axL\lib\site-packages\saspy\java\iomclient\sas.core.jar;C:\Users\bvancil\.virtualenvs\quarto-sas-example-Ugam9axL\lib\site-packages\saspy\java\iomclient\sas.svc.connection.jar;C:\Users\bvancil\.virtualenvs\quarto-sas-example-Ugam9axL\lib\site-packages\saspy\java\iomclient\sas.rutil.jar;C:\Users\bvancil\.virtualenvs\quarto-sas-example-Ugam9axL\lib\site-packages\saspy\java\iomclient\sas.rutil.nls.jar;C:\Users\bvancil\.virtualenvs\quarto-sas-example-Ugam9axL\lib\site-packages\saspy\java\iomclient\sastpj.rutil.jar;C:\Users\bvancil\.virtualenvs\quarto-sas-example-Ugam9axL\lib\site-packages\saspy\java\thirdparty\glassfish-corba-internal-api.jar;C:\Users\bvancil\.virtualenvs\quarto-sas-example-Ugam9axL\lib\site-packages\saspy\java\thirdparty\glassfish-corba-omgapi.jar;C:\Users\bvancil\.virtualenvs\quarto-sas-example-Ugam9axL\lib\site-packages\saspy\java\thirdparty\glassfish-corba-orb.jar;C:\Users\bvancil\.virtualenvs\quarto-sas-example-Ugam9axL\lib\site-packages\saspy\java\thirdparty\pfl-basic.jar;C:\Users\bvancil\.virtualenvs\quarto-sas-example-Ugam9axL\lib\site-packages\saspy\java\thirdparty\pfl-tf.jar" pyiom.saspy2j -host localhost -stdinport 50678 -stdoutport 50679 -stderrport 50680 -zero -lrecl 1048576
ERROR StatusLogger No Log4j 2 configuration file found. Using default configuration (logging only errors to the console), or user programmatically provided configurations. Set system property 'log4j2.debug' to show Log4j 2 internal initialization logging. See https://logging.apache.org/log4j/2.x/manual/configuration.html for instructions on how to configure Log4j 2
We failed in getConnection
The application could not log on to the server "localhost:0". Integrated Windows authentication failed.com.sas.services.connection.LoginException: The application could not log on to the server "localhost:0". Integrated Windows authentication failed.
        at com.sas.services.connection.ClusterEnvelope.getConnection(ClusterEnvelope.java:129)
        at com.sas.services.connection.AggregationKernel.doGetConnection(AggregationKernel.java:242)
        at com.sas.services.connection.ConnectionFactoryKernel.getConnection(ConnectionFactoryKernel.java:325)
        at com.sas.services.connection.ConnectionFactoryShell.getConnection(ConnectionFactoryShell.java:69)
        at com.sas.services.connection.ConnectionFactoryShell.getConnection(ConnectionFactoryShell.java:51)
        at pyiom.saspy2j.main(saspy2j.java:201)
Caused by: org.omg.CORBA.NO_PERMISSION: Access denied.  vmcid: 0x0  minor code: 5  completed: No
        at com.sas.iom.orb.brg.Engine.parseErrorXML(Engine.java:2211)
        at com.sas.iom.orb.brg.Engine.checkForErrorPacket(Engine.java:2032)
        at com.sas.iom.orb.brg.Engine.readPacket(Engine.java:5909)
        at com.sas.iom.orb.brg.Engine.flowSendAuth(Engine.java:4353)
        at com.sas.iom.orb.brg.Engine.flow(Engine.java:717)
        at com.sas.iom.orb.brg.Engine.initClient(Engine.java:676)
        at com.sas.iom.orb.brg.ORBImpl.uri_to_object(ORBImpl.java:114)
        at com.sas.services.connection.ClusterEnvelope.createObject(ClusterEnvelope.java:394)
        at com.sas.services.connection.ClusterEnvelope.getConnection(ClusterEnvelope.java:86)
        ... 5 more
Caused by: com.sas.iom.SASIOMDefs.GenericError: Unexpected error in function AcceptSecurityContext.  Error -2146893044 (The logon attempt failed ).
        at com.sas.iom.orb.brg.Engine.parseErrorXML(Engine.java:2112)
        ... 13 more
```
