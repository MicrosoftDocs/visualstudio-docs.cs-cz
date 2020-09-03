---
title: Referenční dokumentace schématu produktu a balíčku | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- MSBuild.GenerateBootstrapper.CircularIncludes
- MSBuild.ResolveManifestFiles.PublishFileNotFound
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce, product and package files
- Windows Installer, product and package files
- product files [ClickOnce]
- ClickOnce, bootstrapper elements
- package files [Windows Installer]
- product files [Windows Installer]
- package files [ClickOnce]
- Windows Installer, bootstrapper elements
ms.assetid: 5a74878f-b896-4cca-b968-98d00fe78fb0
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2fe0d270593ef526405b0be4cde8bc5da10af413
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188954"
---
# <a name="product-and-package-schema-reference"></a>Referenční schéma balíčku a produktu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Soubor produktu* je manifest XML, který popisuje všechny externí závislosti požadované [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikací. Mezi externí závislosti patří [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] i komponenty a součásti MDAC (Microsoft Data Access Components). Soubor balíčku je podobný souboru produktu, ale používá se k instalaci komponent závislých na jazykové verzi závislosti, jako jsou lokalizovaná sestavení, licenční smlouvy a dokumentace.  
  
 Soubor produktu a balíčky se skládá buď z nejvyšší úrovně `Product` , nebo z `Package` prvku, z nichž každý obsahuje následující prvky.  
  
|Element|Popis|Atributy|  
|-------------|-----------------|----------------|  
|[\<Product> Objekt](../deployment/product-element-bootstrapper.md)|Pro soubory produktu je vyžadován element nejvyšší úrovně.|Žádné|  
|[\<Package> Objekt](../deployment/package-element-bootstrapper.md)|Pro soubory balíčku je vyžadován element nejvyšší úrovně.|`Culture`<br /><br /> `Name`<br /><br /> `EULA`|  
|[\<RelatedProducts> Objekt](../deployment/relatedproducts-element-bootstrapper.md)|Volitelný prvek pro soubory produktu. Ostatní produkty, na které tento produkt buď nainstaluje nebo závisí.|Žádné|  
|[\<InstallChecks> Objekt](../deployment/installchecks-element-bootstrapper.md)|Požadovaný element. Uvádí kontroly závislostí, které se mají v místním počítači provádět během instalace.|Žádné|  
|[\<Commands> Objekt](../deployment/commands-element-bootstrapper.md)|Požadovaný element.  Provede jednu nebo více kontrol instalace, jak je popsáno v tématu `InstallChecks` , a označuje, který balíček se má nainstalovat, aby se kontrola nezdařila.|Žádné|  
|[\<PackageFiles> Objekt](../deployment/packagefiles-element-bootstrapper.md)|Požadovaný element. Obsahuje seznam balíčků, které mohou být nainstalovány tímto procesem instalace.|Žádné|  
|[\<Strings> Objekt](../deployment/strings-element-bootstrapper.md)|Požadovaný element. Ukládá lokalizované verze názvu produktu a chybové řetězce.|Žádné|  
  
## <a name="remarks"></a>Poznámky  
 Schéma balíčku je spotřebováno Setup.exe, což je program, který vygenerovala úloha zaváděcího nástroje MS Build, která obsahuje málo pevně zakódované logiky. Schéma řídí všechny aspekty procesu instalace.  
  
 `InstallChecks` testy, které by setup.exe měly provádět pro existenci daného balíčku. `PackageFiles` Zobrazí seznam všech balíčků, které může instalační proces instalace provést, pokud daný test selže. Každý příkaz v příkazu v příkazech provede jeden z testů popsaných v `InstallChecks` a určí, který `PackageFile` má být spuštěn, pokud test selže. Pomocí `Strings` elementu můžete lokalizovat názvy produktů a chybové zprávy, abyste mohli nainstalovat aplikaci pro libovolný počet jazyků pomocí jediného binárního souboru instalace.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje úplný soubor produktu pro instalaci portálu [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
  
<Product  
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
  ProductCode="Microsoft.Net.Framework.2.0"  
>  
  
    <RelatedProducts>  
        <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />  
    </RelatedProducts>  
  
    <!-- Defines list of files to be copied on build -->  
    <PackageFiles>  
        <PackageFile Name="instmsia.exe" HomeSite="InstMsiAExe" PublicKey="3082010A0282010100AA99BD39A81827F42B3D0B4C3F7C772EA7CBB5D18C0DC23A74D793B5E0A04B3F595ECE454F9A7929F149CC1A47EE55C2083E1220F855F2EE5FD3E0CA96BC30DEFE58C82732D08554E8F09110BBF32BBE19E5039B0B861DF3B0398CB8FD0B1D3C7326AC572BCA29A215908215E277A34052038B9DC270BA1FE934F6F335924E5583F8DA30B620DE5706B55A4206DE59CBF2DFA6BD154771192523D2CB6F9B1979DF6A5BF176057929FCC356CA8F440885558ACBC80F464B55CB8C96774A87E8A94106C7FF0DE968576372C36957B443CF323A30DC1BE9D543262A79FE95DB226724C92FD034E3E6FB514986B83CD0255FD6EC9E036187A96840C7F8E203E6CF050203010001"/>  
        <PackageFile Name="WindowsInstaller-KB884016-v2-x86.exe" HomeSite="Msi30Exe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>  
        <PackageFile Name="dotnetfx.exe" HomeSite="DotNetFXExe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>  
        <PackageFile Name="dotnetchk.exe"/>  
    </PackageFiles>  
  
    <InstallChecks>  
        <ExternalCheck Property="DotNetInstalled" PackageFile="dotnetchk.exe" />  
        <RegistryCheck Property="IEVersion" Key="HKLM\Software\Microsoft\Internet Explorer" Value="Version" />  
    </InstallChecks>  
  
    <!-- Defines how to invoke the setup for the .NET Framework redist -->  
    <!-- TODO: Needs EstrimatedTempSpace, LogFile, and an update of EstimatedDiskSpace -->  
    <Commands Reboot="Defer">  
        <Command PackageFile="instmsia.exe"  
                 Arguments= ' /q /c:"msiinst /delayrebootq"'  
                 EstimatedInstallSeconds="20" >  
            <InstallConditions>  
                <BypassIf Property="VersionNT" Compare="ValueExists"/>  
                <BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="2.0"/>  
            </InstallConditions>  
            <ExitCodes>  
                <ExitCode Value="0" Result="SuccessReboot"/>  
                <ExitCode Value="1641" Result="SuccessReboot"/>  
                <ExitCode Value="3010" Result="SuccessReboot"/>  
                <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
            </ExitCodes>  
        </Command>  
        <Command PackageFile="WindowsInstaller-KB884016-v2-x86.exe"  
                 Arguments= '/quiet /norestart'   
                 EstimatedInstallSeconds="20" >  
          <InstallConditions>  
              <BypassIf Property="Version9x" Compare="ValueExists"/>  
              <BypassIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3"/>  
              <BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="3.0"/>  
              <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>  
          </InstallConditions>  
          <ExitCodes>  
              <ExitCode Value="0" Result="Success"/>  
              <ExitCode Value="1641" Result="SuccessReboot"/>  
              <ExitCode Value="3010" Result="SuccessReboot"/>  
              <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
          </ExitCodes>  
        </Command>  
        <Command PackageFile="dotnetfx.exe"   
             Arguments=' /q:a /c:"install /q /l"'   
             EstimatedInstalledBytes="21000000"   
             EstimatedInstallSeconds="300">  
  
            <!-- These checks determine whether the package is to be installed -->  
            <InstallConditions>  
                <!-- Either of these properties indicates the .NET Framework is already installed -->  
                <BypassIf Property="DotNetInstalled" Compare="ValueNotEqualTo" Value="0"/>  
  
                <!-- Block install if user does not have admin privileges -->  
                <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>  
  
                <!-- Block install on Windows 95 -->  
                <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatformWin9x"/>  
  
                <!-- Block install on Windows 2000 SP 2 or less -->  
                <FailIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3" String="InvalidPlatformWinNT"/>  
  
                <!-- Block install if Internet Explorer 5.01 or greater is not present -->  
                <FailIf Property="IEVersion" Compare="ValueNotExists" String="InvalidPlatformIE" />  
                <FailIf Property="IEVersion" Compare="VersionLessThan" Value="5.01" String="InvalidPlatformIE" />  
  
                <!-- Block install if the platform is not x86 -->  
                <FailIf Property="ProcessorArchitecture" Compare="ValueNotEqualTo" Value="Intel" String="InvalidPlatformArchitecture" />  
            </InstallConditions>  
  
            <ExitCodes>  
                <ExitCode Value="0" Result="Success"/>  
                <ExitCode Value="3010" Result="SuccessReboot"/>  
                <ExitCode Value="4097" Result="Fail" String="AdminRequired"/>  
                <ExitCode Value="4098" Result="Fail" String="WindowsInstallerComponentFailure"/>  
                <ExitCode Value="4099" Result="Fail" String="WindowsInstallerImproperInstall"/>  
                <ExitCode Value="4101" Result="Fail" String="AnotherInstanceRunning"/>  
                <ExitCode Value="4102" Result="Fail" String="OpenDatabaseFailure"/>  
                <ExitCode Value="4113" Result="Fail" String="BetaNDPFailure"/>  
                <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
            </ExitCodes>  
  
        </Command>  
    </Commands>  
</Product>  
```  
  
## <a name="see-also"></a>Viz také  
 [ClickOnce – manifest nasazení](../deployment/clickonce-deployment-manifest.md)   
 [Manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md)
