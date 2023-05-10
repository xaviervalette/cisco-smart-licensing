# Cisco Smart Licensing

Configuration of Smart Licensing on Cisco device


## Smart Licensing via direct connect

<p align="center">
<img width="700" alt="image" src="https://github.com/xaviervalette/cisco-smart-licensing/assets/28600326/801d1aba-3cfa-4bca-9cab-e85057635ae7">
</p>

### Check the current state of the Smart Licensing on your device

```console
show license status                                                                                                          
```
 <details>
   <summary> 
       <ins>Expected output</ins>
  </summary>
  
```console
csr1#sh license status
Smart Licensing is ENABLED

Utility:
  Status: DISABLED

Data Privacy:
  Sending Hostname: yes
    Callhome hostname privacy: DISABLED
    Smart Licensing hostname privacy: DISABLED
  Version privacy: DISABLED

Transport:
  Type: Callhome

Registration:
  Status: UNREGISTERED
  Export-Controlled Functionality: NOT ALLOWED

License Authorization: 
  Status: No Licenses in Use

Export Authorization Key:
  Features Authorized:
    <none>

Miscellaneous:
  Custom Id: <empty>
  ```
      
</details>
      
### Generate a token on the CSSM for your device

<p align="center">
<img width="800" alt="image" src="https://github.com/xaviervalette/cisco-smart-licensing/assets/28600326/95a80da9-20a8-46b9-b4f5-c4c2243bec39">
      </p>


### On your device, use the token (created on the CSSM) to register your device

```console
license smart register idtoken <your_token>
```
 <details>
   <summary> 
       <ins>Expected output</ins>
  </summary>
  
  ```console
  csr1#license smart register idtoken ODFjNWU3NjUtMDYwZS0...
  Registration process is in progress. Use the 'show license status' command to check the progress and result
  ```
</details>

### Check the updated state of the Smart Licensing on your device

On the device:
```console
show license status                                                                                                          
```

 <details>
   <summary> 
       <ins>Expected output</ins>
  </summary>
  
```console
csr1#sh license status                                                                                                          
Smart Licensing is ENABLED

Utility:
  Status: DISABLED

Data Privacy:
  Sending Hostname: yes
    Callhome hostname privacy: DISABLED
    Smart Licensing hostname privacy: DISABLED
  Version privacy: DISABLED

Transport:
  Type: Callhome

Registration:
  Status: REGISTERED
  Smart Account: Cisco Demo Internal Customer Smart Account
  Virtual Account: CML-xvalette
  Export-Controlled Functionality: ALLOWED
  Initial Registration: SUCCEEDED on May 10 16:39:56 2023 UTC
  Last Renewal Attempt: None
  Next Renewal Attempt: Nov 06 16:39:56 2023 UTC
  Registration Expires: May 09 15:40:46 2024 UTC
          
License Authorization: 
  Status: AUTHORIZED on May 10 16:40:00 2023 UTC
  Last Communication Attempt: SUCCEEDED on May 10 16:40:00 2023 UTC
  Next Communication Attempt: Jun 09 16:40:00 2023 UTC
  Communication Deadline: Aug 08 15:40:51 2023 UTC

Export Authorization Key:
  Features Authorized:
    <none>

Miscellaneous:
  Custom Id: <empty>
```
</details>

On the CSSM:

<p align="center">
<img width="800" alt="image" src="https://github.com/xaviervalette/cisco-smart-licensing/assets/28600326/b964a803-6235-4339-93e0-c181e3b0e198">
      </p>

