---
title: '&lt;Command – &gt; element (zaváděcí nástroj) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Commands> element [bootstrapper]
ms.assetid: e61d5787-fe1f-4ebf-b0cf-0d7909be7ffb
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: af10c9e0b26a6ef2c8e7a98bc345b8e86017682b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205337"
---
# <a name="ltcommandsgt-element-bootstrapper"></a>&lt;Commands – &gt; element (zaváděcí nástroj)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Commands`Element implementuje testy popsané prvky pod `InstallChecks` prvkem a deklaruje, který balíček [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] by měl zaváděcí nástroj nainstalovat, pokud se test nezdařil.  
  
## <a name="syntax"></a>Syntax  
  
```  
<Commands  
    Reboot  
>  
    <Command  
        PackageFile  
        Arguments  
        EstimatedInstallSeconds  
        EstimatedDiskBytes  
        EstimatedTempBytes  
        Log  
    >  
        <InstallConditions>  
            <BypassIf   
                Property  
                Compare  
                Value  
                Schedule  
            />  
            <FailIf   
                Property  
                Compare  
                Value  
                String  
                Schedule  
            />  
        </InstallConditions>  
        <ExitCodes>  
            <ExitCode   
                Value  
                Result  
                String  
            />  
        </ExitCodes>  
    </Command>  
</Commands>  
```  
  
## <a name="elements-and-attributes"></a>Elementy a atributy  
 `Commands`Element je povinný. Element má následující atribut.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Reboot`|Nepovinný parametr. Určuje, zda má být systém restartován, pokud některý z balíčků vrátí ukončovací kód pro restartování. V následujícím seznamu jsou uvedeny platné hodnoty:<br /><br /> `Defer`. Restart se odvozuje až do doby v budoucnosti.<br /><br /> `Immediate`. Způsobí okamžité restartování, pokud jeden z balíčků vrátil ukončovací kód pro restartování.<br /><br /> `None`. Způsobí ignorování všech požadavků na restartování.<br /><br /> Výchozí formát je `Immediate`.|  
  
## <a name="command"></a>Příkaz  
 `Command`Prvek je podřízeným prvkem `Commands` elementu. `Commands`Element může obsahovat jeden nebo více `Command` prvků. Element má následující atributy.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`PackageFile`|Povinná hodnota. Název balíčku, který se má nainstalovat, má jednu nebo více podmínek určených parametrem `InstallConditions` return false. Balíček musí být definován ve stejném souboru pomocí `PackageFile` elementu.|  
|`Arguments`|Nepovinný parametr. Sada argumentů příkazového řádku, která se má předat do souboru balíčku.|  
|`EstimatedInstallSeconds`|Nepovinný parametr. Odhadovaná doba (v sekundách) bude trvat instalaci balíčku. Tato hodnota určuje velikost indikátoru průběhu, který zaváděcí nástroj zobrazí uživateli. Výchozí hodnota je 0, v takovém případě se nezadá žádný časový odhad.|  
|`EstimatedDiskBytes`|Nepovinný parametr. Odhadované množství místa na disku (v bajtech), které bude balíček zabírat po dokončení instalace. Tato hodnota se používá v požadavcích na volné místo na pevném disku, kterou nástroj pro uživatele zobrazí. Výchozí hodnota je 0. v takovém případě zaváděcí nástroj nezobrazuje žádné požadavky na volné místo na pevném disku.|  
|`EstimatedTempBytes`|Nepovinný parametr. Odhadovaná velikost dočasného místa na disku (v bajtech), které bude balíček vyžadovat.|  
|`Log`|Nepovinný parametr. Cesta k souboru protokolu, který vygeneruje balíček, relativně ke kořenovému adresáři balíčku.|  
  
## <a name="installconditions"></a>InstallConditions  
 `InstallConditions`Prvek je podřízeným prvkem `Command` elementu. Každý `Command` prvek může mít maximálně jeden `InstallConditions` element. Pokud žádný `InstallConditions` prvek neexistuje, balíček určený pomocí `Condition` bude vždy spuštěn.  
  
## <a name="bypassif"></a>BypassIf  
 `BypassIf`Element je podřízeným prvkem `InstallConditions` prvku a popisuje kladnou podmínku, za kterou by neměl být příkaz spuštěn. Každý `InstallConditions` prvek může mít nula nebo více `BypassIf` prvků.  
  
 `BypassIf` má následující atributy.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Property`|Povinná hodnota. Název vlastnosti, která má být testována. Vlastnost již musí být definována podřízeným `InstallChecks` elementu. Další informace naleznete v tématu [ \<InstallChecks> element](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Povinná hodnota. Typ porovnání, který má být proveden. V následujícím seznamu jsou uvedeny platné hodnoty:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Povinná hodnota. Hodnota, která má být porovnána s vlastností.|  
|`Schedule`|Nepovinný parametr. Název `Schedule` značky definující, kdy má být toto pravidlo vyhodnoceno.|  
  
## <a name="failif"></a>FailIf  
 `FailIf`Prvek je podřízeným prvkem `InstallConditions` prvku a popisuje kladnou podmínku, za níž by se měla zastavit instalace. Každý `InstallConditions` prvek může mít nula nebo více `FailIf` prvků.  
  
 `FailIf` má následující atributy.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Property`|Povinná hodnota. Název vlastnosti, která má být testována. Vlastnost již musí být definována podřízeným `InstallChecks` elementu. Další informace naleznete v tématu [ \<InstallChecks> element](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Povinná hodnota. Typ porovnání, který má být proveden. V následujícím seznamu jsou uvedeny platné hodnoty:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Povinná hodnota. Hodnota, která má být porovnána s vlastností.|  
|`String`|Nepovinný parametr. Text, který se má uživateli zobrazit při selhání.|  
|`Schedule`|Nepovinný parametr. Název `Schedule` značky definující, kdy má být toto pravidlo vyhodnoceno.|  
  
## <a name="exitcodes"></a>ExitCodes  
 `ExitCodes`Prvek je podřízeným prvkem `Command` elementu. `ExitCodes`Element obsahuje jeden nebo více `ExitCode` prvků, které určují, co by měla instalace dělat v reakci na ukončovací kód z balíčku. Pod prvkem může být jeden volitelný `ExitCode` element `Command` . `ExitCodes` nemá žádné atributy.  
  
## <a name="exitcode"></a>ExitCode  
 `ExitCode`Prvek je podřízeným prvkem `ExitCodes` elementu. `ExitCode`Prvek určuje, co by měl instalace dělat v reakci na ukončovací kód z balíčku. `ExitCode` neobsahuje žádné podřízené elementy a má následující atributy.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Value`|Povinná hodnota. Hodnota ukončovacího kódu, na kterou `ExitCode` se vztahuje tento prvek.|  
|`Result`|Povinná hodnota. Jak by měla instalace reagovat na tento ukončovací kód. V následujícím seznamu jsou uvedeny platné hodnoty:<br /><br /> `Success`. Označí balíček jako úspěšně nainstalovaný.<br /><br /> `SuccessReboot`. Označí balíček jako úspěšně nainstalovaný a vydá pokyn k restartování systému.<br /><br /> `Fail`. Označí balíček jako neúspěšný.<br /><br /> `FailReboot`. Označí balíček jako neúspěšný a vydá pokyn k restartování systému.|  
|`String`|Nepovinný parametr. Hodnota, která se má zobrazit uživateli v reakci na tento ukončovací kód.|  
|`FormatMessageFromSystem`|Nepovinný parametr. Určuje, zda se má použít chybová zpráva poskytnutá systémem, která odpovídá ukončovacímu kódu, nebo použijte hodnotu poskytnutou v `String` . Platné hodnoty jsou `true` , což znamená, že použijte chybu poskytnutou systémem a `false` , která znamená použít řetězec poskytnutý pomocí `String` . Výchozí formát je `false`. Pokud tato vlastnost není `false` , ale není `String` nastavená, použije se chyba poskytovaná systémem.|  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu definuje příkazy pro instalaci .NET Framework 2,0.  
  
```  
<Commands Reboot="Immediate">  
    <Command PackageFile="instmsia.exe"  
             Arguments= ' /q /c:"msiinst /delayrebootq"'  
             EstimatedInstallSeconds="20" >  
        <InstallConditions>  
           <BypassIf Property="VersionNT" Compare="ValueExists"/>  
             BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="2.0"/>  
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
  
            <!-- Block install if user does not have adminpermissions -->  
            <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>  
  
            <!-- Block install on Windows 95 -->  
            <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatformWin9x"/>  
  
            <!-- Block install on Windows 2000 SP 2 or less -->  
            <FailIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3" String="InvalidPlatformWinNT"/>  
  
            <!-- Block install if Internet Explorer 5.01 or later is not present -->  
            <FailIf Property="IEVersion" Compare="ValueNotExists" String="InvalidPlatformIE" />  
            <FailIf Property="IEVersion" Compare="VersionLessThan" Value="5.01" String="InvalidPlatformIE" />  
  
            <!-- Block install if the operating system does not support x86 -->  
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
```  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na schéma produktu a balíčku](../deployment/product-and-package-schema-reference.md)   
 [\<InstallChecks> Objekt](../deployment/installchecks-element-bootstrapper.md)
