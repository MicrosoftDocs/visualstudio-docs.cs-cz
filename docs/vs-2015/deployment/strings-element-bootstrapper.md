---
title: '&lt;Strings – &gt; element (zaváděcí nástroj) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- MSBuild.GenerateBootstrapper.NoStringsForCulture
- MSBuild.GenerateBootstrapper.ProductCultureNotFound
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Strings> element [bootstrapper]
ms.assetid: d5ea3613-5fc9-4a11-bef3-46a01178bf60
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dd799020e50121e2f3e9a6ba7ad90fd79a1241cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62421522"
---
# <a name="ltstringsgt-element-bootstrapper"></a>&lt;Strings – &gt; element (zaváděcí nástroj)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Definuje lokalizované řetězce pro názvy produktů, názvy balíčků a chybové zprávy instalace.  
  
## <a name="syntax"></a>Syntax  
  
```  
<Strings>  
    <String  
        Name  
    >  
    </String>  
</Strings>  
```  
  
## <a name="elements-and-attributes"></a>Elementy a atributy  
 `Strings`Prvek je podřízeným prvkem `Package` elementu. Nemá žádné atributy.  
  
## <a name="string"></a>Řetězec  
 `String`Prvek je podřízeným prvkem `Strings` elementu. `Strings`Element může obsahovat jeden nebo více `String` prvků.  
  
 `String` má následující atribut.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Name`|Povinná hodnota. Název řetězce.|  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu určuje všechny anglické řetězce pro [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] instalační program.  
  
```  
<Strings>  
    <String Name="DisplayName">.NET Framework 2.0</String>  
    <String Name="Culture">en</String>  
    <String Name="AdminRequired">Administrator permissions are required to install the .NET Framework 2.0. Contact your administrator.</String>  
    <String Name="InvalidPlatformWin9x">Installation of the .NET Framework 2.0 is not supported on Windows 95. Contact your application vendor.</String>  
    <String Name="InvalidPlatformWinNT">Installation of the .NET Framework 2.0 is not supported on Windows NT 4.0. Contact your application vendor.</String>  
    <String Name="InvalidPlatformIE">Installation of the .NET Framework 2.0 requires Internet Explorer 5.01 or greater. Contact your application vendor.</String>  
    <String Name="InvalidPlatformArchitecture">This version of the .NET Framework 2.0 is not supported on a 64-bit operating system. Contact your application vendor.</String>  
    <String Name="WindowsInstallerImproperInstall">Due to an error with Windows Installer, the installation of the .NET Framework 2.0 cannot proceed.</String>  
    <String Name="AnotherInstanceRunning">Another instance of setup is already running. The running instance must complete before this setup can proceed.</String>  
    <String Name="BetaNDPFailure">A beta version of the .NET Framework was detected on the computer. Uninstall any previous beta versions of .NET Framework before continuing.</String>  
    <String Name="GeneralFailure">A failure occurred attempting to install the .NET Framework 2.0.</String>  
    <String Name="DotNetFXExe">http://go.microsoft.com/fwlink/?LinkId=37283</String>  
    <String Name="InstMsiAExe">http://go.microsoft.com/fwlink/?LinkId=37285</String>  
    <String Name="Msi30Exe">http://go.microsoft.com/fwlink/?LinkId=37287</String>  
</Strings>  
```  
  
## <a name="see-also"></a>Viz také  
 [\<Package> Objekt](../deployment/package-element-bootstrapper.md)
