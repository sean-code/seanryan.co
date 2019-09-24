![](https://raw.githubusercontent.com/sean-code/seanryan.co/master/images/posts/2018-07-19-windows-10-now-offering-2fa/two-factor-multi-factor-authenication-768x502.jpg)
If you have Windows 10 Pro 1709 or above, you can now take advantage of a surprising new feature part of Windows Hello for Business dubbed  Multifactor Unlock.

I’ve been looking for a viable multifactor authentication solution for Windows for awhile now, looking at options like Duo Security and Yubikey(both which I’ve used and love). Unfortunately, [Duo requires an internet connection to work](https://community.duo.com/t/offline-authentication-without-bypass-enabled/909), and [Yubikey doesn’t work when your system is locked](https://support.yubico.com/support/solutions/articles/15000006472)(It only works on initial boot).

Windows Hello Multifactor Unlock  can work with a PIN(can be alphanumeric), fingerprint, facial recognition, and/or trusted signal(cell phone proximity or network location). Microsoft breaks down the [information here](https://docs.microsoft.com/en-us/windows/security/identity-protection/hello-for-business/feature-multifactor-unlock).

The **_first_** unlock factor can be a: PIN, Fingerprint, or Facial Recognition.

The **_second_** unlock factor can be a: Trusted Signal or PIN

The failsafe feature(in case your face melts or your fingers go missing) is your main account password. So in theory, you can make your pin be simple and your main account password extra strong.

In regards to “Trusted Signal”, it can be the bluetooth signal from your phone, another computer, wearable and a few others, or if can be a “trusted network”, which possibly could be your work/home network. You can definitely get into the weeds, but for simplicity, a bluetooth signal from your paired phone may be the easiest. I personally like the fingerprint + PIN solution. If you don’t have a fingerprint reader on your computer, a bluetooth signal from your paired phone or using your face can work. Note: facial recognition requires a special IR camera.

The following group policy settings can be modified to achieve this solution:
![](https://raw.githubusercontent.com/sean-code/seanryan.co/master/images/posts/2018-07-19-windows-10-now-offering-2fa/gpme.png)
![](https://raw.githubusercontent.com/sean-code/seanryan.co/master/images/posts/2018-07-19-windows-10-now-offering-2fa/gp-setting.png)


The special GUIDs from Microsoft’s website are as followed:

|Credential Provider| 	GUID|
|-------------------|-------|
|PIN | 	{D6886603-9D2F-4EB2-B667-1971041FA96B}|
|Fingerprint| 	{BEC09223-B018-416D-A0AC-523971B639F5}|
|Facial Recognition| 	{8AF662BF-65A0-4D0A-A540-A338A999D36F}|
|Trusted Signal (Phone proximity, Network location)| 	{27FBDB57-B613-4AF2-9D7E-4FA7A66C21AD}|

More information on this new security feature is on [their website](https://docs.microsoft.com/en-us/windows/security/identity-protection/hello-for-business/feature-multifactor-unlock) including more details on Trusted Signal.

Be sure to let me know what you thoughts are on this and if and/or how you plan on using the feature.