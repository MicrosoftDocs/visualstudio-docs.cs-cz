---
title: '&lt;Příkazy&gt; – Element (zaváděcí nástroj) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: wpickett
ms.openlocfilehash: 309f93658cee6663c2b5673c03c6621330e7fa39
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49276572"
---
# <a name="ltcommandsgt-element-bootstrapper"></a>&lt;Příkazy&gt; – Element (zaváděcí nástroj)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Commands` Prvek implementuje testy, které jsou popsané prvky pod `InstallChecks` elementu a deklaruje balíčky, které [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] zaváděcího nástroje by měla nainstalovat, pokud se test nezdaří.  
  
## <a name="syntax"></a>Syntaxe  
  
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
 `Commands` Je vyžadován element. Element má tento atribut.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Reboot`|Volitelné. Určuje, zda by měl restartování systému, pokud žádný z balíčků vrátí kód ukončení restartování. Následující seznam uvádí platné hodnoty:<br /><br /> `Defer`. Restart je odložena až do později.<br /><br /> `Immediate`. Pokud některý z balíčků vrátí kód ukončení restartování způsobí, že okamžité restartování.<br /><br /> `None`. Způsobí, že všechny požadavky na Ignorovat restartování.<br /><br /> Výchozí hodnota je `Immediate`.|  
  
## <a name="command"></a>Příkaz  
 `Command` Prvek je podřízený prvek `Commands` elementu. A `Commands` prvek může mít jeden nebo více `Command` elementy. Element má následující atributy.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`PackageFile`|Požadováno. Jeden nebo více z určených podle podmínek by měl název balíčku pro instalaci `InstallConditions` vrátí false. Balíček musí být definován ve stejném souboru s použitím `PackageFile` elementu.|  
|`Arguments`|Volitelné. Sada argumenty příkazového řádku k předání do souboru balíčku.|  
|`EstimatedInstallSeconds`|Volitelné. Odhadovaný čas v sekundách, bude trvat k instalaci balíčku. Tato hodnota určuje velikost indikátoru průběhu, který zaváděcí nástroj zobrazí uživateli. Výchozí hodnota je 0, v takovém případě žádný čas zadaný odhad.|  
|`EstimatedDiskBytes`|Volitelné. Odhadovaná velikost místa na disku v bajtech, které budou zaměstnávat balíčku po instalaci je dokončena. Tato hodnota se používá v pevném místo na disku, které zaváděcí nástroj zobrazí uživateli. Výchozí hodnota je 0, ve kterém zaváděcí nejsou zobrazeny žádné požadavky na místo pevného disku.|  
|`EstimatedTempBytes`|Volitelné. Odhadovaná velikost dočasného prostoru na disku v bajtech, která bude vyžadovat balíček.|  
|`Log`|Volitelné. Cesta k souboru protokolu, který generuje balíček, vzhledem k kořenový adresář balíčku.|  
  
## <a name="installconditions"></a>InstallConditions  
 `InstallConditions` Element je podřízeným prvkem `Command` elementu. Každý `Command` prvek může mít maximálně jeden `InstallConditions` elementu. Pokud ne `InstallConditions` existuje element, balíček určený pomocí `Condition` bude vždy spuštěn.  
  
## <a name="bypassif"></a>BypassIf  
 `BypassIf` Element je podřízeným prvkem `InstallConditions` prvek a popisuje pozitivní podmínku, pod kterým by neměl být spouštěn příkazu. Každý `InstallConditions` prvek může mít nula nebo více `BypassIf` elementy.  
  
 `BypassIf` má následující atributy.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Property`|Požadováno. Název vlastnosti pro testování. Vlastnost musí být dříve definována podřízený `InstallChecks` elementu. Další informace najdete v tématu [ \<InstallChecks > Element](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Požadováno. Typ porovnání k provedení. Následující seznam uvádí platné hodnoty:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Požadováno. Hodnota určená k porovnání s vlastností.|  
|`Schedule`|Volitelné. Název `Schedule` značka, která definuje, kdy by se mělo vyhodnotit pravidlo.|  
  
## <a name="failif"></a>FailIf  
 `FailIf` Element je podřízeným prvkem `InstallConditions` prvek a popisuje pozitivní podmínku, pod kterým by se měla zastavit instalaci. Každý `InstallConditions` prvek může mít nula nebo více `FailIf` elementy.  
  
 `FailIf` má následující atributy.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Property`|Požadováno. Název vlastnosti pro testování. Vlastnost musí být dříve definována podřízený `InstallChecks` elementu. Další informace najdete v tématu [ \<InstallChecks > Element](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Požadováno. Typ porovnání k provedení. Následující seznam uvádí platné hodnoty:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Požadováno. Hodnota určená k porovnání s vlastností.|  
|`String`|Volitelné. Text zobrazený uživateli, nebude úspěšná.|  
|`Schedule`|Volitelné. Název `Schedule` značka, která definuje, kdy by se mělo vyhodnotit pravidlo.|  
  
## <a name="exitcodes"></a>ExitCodes  
 `ExitCodes` Element je podřízeným prvkem `Command` elementu. `ExitCodes` Element obsahuje jeden nebo více `ExitCode` prvky, které určují, co dělat v reakci na ukončovací kód z balíčku instalace. Může dojít k jednomu volitelné `ExitCode` element pod `Command` elementu. `ExitCodes` nemá žádné atributy.  
  
## <a name="exitcode"></a>Ukončovací kód  
 `ExitCode` Element je podřízeným prvkem `ExitCodes` elementu. `ExitCode` Element určuje, co dělat v reakci na ukončovací kód z balíčku instalace. `ExitCode` neobsahuje žádné podřízené prvky a má následující atributy.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Value`|Požadováno. Hodnotu ukončovacího kódu, ke kterému je tento `ExitCode` vztahuje k elementu.|  
|`Result`|Požadováno. Jak by instalace měla reagovat na tento kód ukončení. Následující seznam uvádí platné hodnoty:<br /><br /> `Success`. Příznaky balíčku jako úspěšně nainstalován.<br /><br /> `SuccessReboot`. Označuje jako úspěšně nainstaloval balíček a dává pokyn k restartování systému.<br /><br /> `Fail`. Balíček se označuje jako neúspěšný.<br /><br /> `FailReboot`. Příznaky balíčku jako neúspěšný a dává pokyn k restartování systému.|  
|`String`|Volitelné. Hodnota, která se budou zobrazovat uživateli v odpovědi na tento kód ukončení.|  
|`FormatMessageFromSystem`|Volitelné. Určuje, jestli se má použít poskytované systémem chybová zpráva odpovídá ukončovací kód, nebo použijte hodnotu podle `String`. Platné hodnoty jsou `true`, což znamená, že použití poskytovaných systémem chyby, a `false`, což znamená, že použití řetězce poskytované `String`. Výchozí hodnota je `false`. Pokud je tato vlastnost `false`, ale `String` není nastaven, chyba poskytnuté systémem, který se použije.|  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu definuje příkazy pro instalaci rozhraní .NET Framework 2.0.  
  
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
 [Referenční schéma balíčku a produktu](../deployment/product-and-package-schema-reference.md)   
 [\<InstallChecks > – Element](../deployment/installchecks-element-bootstrapper.md)



