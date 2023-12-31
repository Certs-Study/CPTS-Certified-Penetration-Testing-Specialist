# 🟢 RPC

```
rpcclient -N -U "alex" 10.129.202.41
```

```
---------------         ----------------------
       UNIXINFO       getpwuid         Get shell and homedir
       uidtosid         Convert uid to sid
---------------         ----------------------
         MDSSVC
fetch_properties                Fetch connection properties
fetch_attributes                Fetch attributes for a CNID
---------------         ----------------------
        CLUSAPI
clusapi_open_cluster            Open cluster
clusapi_get_cluster_name                Get cluster name
clusapi_get_cluster_version             Get cluster version
clusapi_get_quorum_resource             Get quorum resource
clusapi_create_enum             Create enum query
clusapi_create_enumex           Create enumex query
clusapi_open_resource           Open cluster resource
clusapi_online_resource         Set cluster resource online
clusapi_offline_resource                Set cluster resource offline
clusapi_get_resource_state              Get cluster resource state
clusapi_get_cluster_version2            Get cluster version2
clusapi_pause_node              Pause cluster node
clusapi_resume_node             Resume cluster node
---------------         ----------------------
        WITNESS
GetInterfaceList                List the interfaces to which witness client connections can be made
       Register         Register for resource state change notifications of a NetName and IPAddress
     UnRegister         Unregister for notifications from the server</para></listitem></varlistentry>
    AsyncNotify         Request notification of registered resource changes from the server
     RegisterEx         Register for resource state change notifications of a NetName, ShareName and multiple IPAddresses
---------------         ----------------------
          FSRVP
fss_is_path_sup         Check whether a share supports shadow-copy requests
fss_get_sup_version             Get supported FSRVP version from server
fss_create_expose               Request shadow-copy creation and exposure
     fss_delete         Request shadow-copy share deletion
fss_has_shadow_copy             Check for an associated share shadow-copy
fss_get_mapping         Get shadow-copy share mapping information
fss_recovery_complete           Flag read-write snapshot as recovery complete, allowing further shadow-copy requests
---------------         ----------------------
         WINREG
 winreg_enumkey         Enumerate Keys
querymultiplevalues             Query multiple values
querymultiplevalues2            Query multiple values
---------------         ----------------------
       EVENTLOG
eventlog_readlog                Read Eventlog
eventlog_numrecord              Get number of records
eventlog_oldestrecord           Get oldest record
eventlog_reportevent            Report event
eventlog_reporteventsource              Report event and source
eventlog_registerevsource               Register event source
eventlog_backuplog              Backup Eventlog File
eventlog_loginfo                Get Eventlog Information
---------------         ----------------------
        DRSUAPI
   dscracknames         Crack Name
    dsgetdcinfo         Get Domain Controller Info
 dsgetncchanges         Get NC Changes
dswriteaccountspn               Write Account SPN
---------------         ----------------------
         NTSVCS
ntsvcs_getversion               Query NTSVCS version
ntsvcs_validatedevinst          Query NTSVCS device instance
ntsvcs_hwprofflags              Query NTSVCS HW prof flags
ntsvcs_hwprofinfo               Query NTSVCS HW prof info
ntsvcs_getdevregprop            Query NTSVCS device registry property
ntsvcs_getdevlistsize           Query NTSVCS device list size
ntsvcs_getdevlist               Query NTSVCS device list
---------------         ----------------------
         WKSSVC
wkssvc_wkstagetinfo             Query WKSSVC Workstation Information
wkssvc_getjoininformation               Query WKSSVC Join Information
wkssvc_messagebuffersend                Send WKSSVC message
wkssvc_enumeratecomputernames           Enumerate WKSSVC computer names
wkssvc_enumerateusers           Enumerate WKSSVC users
---------------         ----------------------
       SHUTDOWN
---------------         ----------------------
       EPMAPPER
         epmmap         Map a binding
      epmlookup         Lookup bindings
---------------         ----------------------
           ECHO
     echoaddone         Add one to a number
       echodata         Echo data
       sinkdata         Sink data
     sourcedata         Source data
---------------         ----------------------
            DFS
     dfsversion         Query DFS support
         dfsadd         Add a DFS share
      dfsremove         Remove a DFS share
     dfsgetinfo         Query DFS share info
        dfsenum         Enumerate dfs shares
      dfsenumex         Enumerate dfs shares
---------------         ----------------------
         SRVSVC
        srvinfo         Server query info
   netshareenum         Enumerate shares
netshareenumall         Enumerate all shares
netsharegetinfo         Get Share Info
netsharesetinfo         Set Share Info
netsharesetdfsflags             Set DFS flags
    netfileenum         Enumerate open files
   netremotetod         Fetch remote time of day
netnamevalidate         Validate sharename
  netfilegetsec         Get File security
     netsessdel         Delete Session
    netsessenum         Enumerate Sessions
    netdiskenum         Enumerate Disks
    netconnenum         Enumerate Connections
    netshareadd         Add share
    netsharedel         Delete share
---------------         ----------------------
       NETLOGON
     logonctrl2         Logon Control 2
   getanydcname         Get trusted DC name
      getdcname         Get trusted PDC name
  dsr_getdcname         Get trusted DC name
dsr_getdcnameex         Get trusted DC name
dsr_getdcnameex2                Get trusted DC name
dsr_getsitename         Get sitename
dsr_getforesttrustinfo          Get Forest Trust Info
      logonctrl         Logon Control
       samlogon         Sam Logon
change_trust_pw         Change Trust Account Password
    gettrustrid         Get trust rid
dsr_enumtrustdom                Enumerate trusted domains
dsenumdomtrusts         Enumerate all trusted domains in an AD forest
deregisterdnsrecords            Deregister DNS records
netrenumtrusteddomains          Enumerate trusted domains
netrenumtrusteddomainsex                Enumerate trusted domains
getdcsitecoverage               Get the Site-Coverage from a DC
   capabilities         Return Capabilities
logongetdomaininfo              Return LogonGetDomainInfo
---------------         ----------------------
IRemoteWinspool
winspool_AsyncOpenPrinter               Open printer handle
winspool_AsyncCorePrinterDriverInstalled                Query Core Printer Driver Installed
---------------         ----------------------
        SPOOLSS
      adddriver         Add a print driver
     addprinter         Add a printer
      deldriver         Delete a printer driver
    deldriverex         Delete a printer driver with files
       enumdata         Enumerate printer data
     enumdataex         Enumerate printer data for a key
        enumkey         Enumerate printer keys
       enumjobs         Enumerate print jobs
         getjob         Get print job
         setjob         Set print job
      enumports         Enumerate printer ports
    enumdrivers         Enumerate installed printer drivers
   enumprinters         Enumerate printers
        getdata         Get print driver data
      getdataex         Get printer driver data with keyname
      getdriver         Get print driver information
   getdriverdir         Get print driver upload directory
getdriverpackagepath            Get print driver package download directory
     getprinter         Get printer info
    openprinter         Open printer handle
 openprinter_ex         Open printer handle
      setdriver         Set printer driver
getprintprocdir         Get print processor directory
        addform         Add form
        setform         Set form
        getform         Get form
     deleteform         Delete form
      enumforms         Enumerate forms
     setprinter         Set printer comment
 setprintername         Set printername
 setprinterdata         Set REG_SZ printer data
       rffpcnex         Rffpcnex test
     printercmp         Printer comparison test
      enumprocs         Enumerate Print Processors
enumprocdatatypes               Enumerate Print Processor Data Types
   enummonitors         Enumerate Print Monitors
createprinteric         Create Printer IC
playgdiscriptonprinteric                Create Printer IC
getcoreprinterdrivers           Get CorePrinterDriver
enumpermachineconnections               Enumerate Per Machine Connections
addpermachineconnection         Add Per Machine Connection
delpermachineconnection         Delete Per Machine Connection
---------------         ----------------------
           SAMR
      queryuser         Query user info
     querygroup         Query group info
queryusergroups         Query user groups
queryuseraliases                Query user aliases
  querygroupmem         Query group membership
  queryaliasmem         Query alias membership
 queryaliasinfo         Query alias info
    deletealias         Delete an alias
  querydispinfo         Query display info
 querydispinfo2         Query display info
 querydispinfo3         Query display info
   querydominfo         Query domain info
   enumdomusers         Enumerate domain users
  enumdomgroups         Enumerate domain groups
  enumalsgroups         Enumerate alias groups
    enumdomains         Enumerate domains
  createdomuser         Create domain user
 createdomgroup         Create domain group
 createdomalias         Create domain alias
 samlookupnames         Look up names
  samlookuprids         Look up names
 deletedomgroup         Delete domain group
  deletedomuser         Delete domain user
 samquerysecobj         Query SAMR security object
   getdompwinfo         Retrieve domain password info
getusrdompwinfo         Retrieve user domain password info
   lookupdomain         Lookup Domain Name
      chgpasswd         Change user password
     chgpasswd2         Change user password
     chgpasswd3         Change user password
     chgpasswd4         Change user password
 getdispinfoidx         Get Display Information Index
    setuserinfo         Set user info
   setuserinfo2         Set user info2
---------------         ----------------------
      LSARPC-DS
  dsroledominfo         Get Primary Domain Information
---------------         ----------------------
         LSARPC
       lsaquery         Query info policy
     lookupsids         Convert SIDs to names
    lookupsids3         Convert SIDs to names
lookupsids_level                Convert SIDs to names
    lookupnames         Convert names to SIDs
   lookupnames4         Convert names to SIDs
lookupnames_level               Convert names to SIDs
      enumtrust         Enumerate trusted domains
      enumprivs         Enumerate privileges
    getdispname         Get the privilege name
     lsaenumsid         Enumerate the LSA SIDS
lsacreateaccount                Create a new lsa account
lsaenumprivsaccount             Enumerate the privileges of an SID
lsaenumacctrights               Enumerate the rights of an SID
     lsaaddpriv         Assign a privilege to a SID
     lsadelpriv         Revoke a privilege from a SID
lsaaddacctrights                Add rights to an account
lsaremoveacctrights             Remove rights from an account
lsalookupprivvalue              Get a privilege value given its name
 lsaquerysecobj         Query LSA security object
lsaquerytrustdominfo            Query LSA trusted domains info (given a SID)
lsaquerytrustdominfobyname              Query LSA trusted domains info (given a name), only works for Windows > 2k
lsaquerytrustdominfobysid               Query LSA trusted domains info (given a SID)
lsasettrustdominfo              Set LSA trusted domain info
    getusername         Get username
   createsecret         Create Secret
   deletesecret         Delete Secret
    querysecret         Query Secret
      setsecret         Set Secret
retrieveprivatedata             Retrieve Private Data
storeprivatedata                Store Private Data
 createtrustdom         Create Trusted Domain
 deletetrustdom         Delete Trusted Domain
---------------         ----------------------
GENERAL OPTIONS
           help         Get help on commands
              ?         Get help on commands
     debuglevel         Set debug level
          debug         Set debug level
           list         List available commands on <pipe>
           exit         Exit program
           quit         Exit program
           sign         Force RPC pipe connections to be signed
           seal         Force RPC pipe connections to be sealed
         packet         Force RPC pipe connections with packet authentication level
       schannel         Force RPC pipe connections to be sealed with 'schannel'. Assumes valid machine account to this domain controller.
   schannelsign         Force RPC pipe connections to be signed (not sealed) with 'schannel'.  Assumes valid machine account to this domain controller.
        timeout         Set timeout (in milliseconds) for RPC operations
      transport         Choose ncacn transport for RPC operations
           none         Force RPC pipe connections to have no special properties

```
