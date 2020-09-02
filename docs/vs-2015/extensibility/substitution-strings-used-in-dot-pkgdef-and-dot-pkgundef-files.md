---
title: Náhradní řetězce použité v. Pkgdef a. Soubory pkgundef | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .pkgdef and .pkgundef files
ms.assetid: b1755d63-d794-4fd7-864b-70a9684881c2
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 47434d9d1dfcedeeaea330b1d65645d7a632c6e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160532"
---
# <a name="substitution-strings-used-in-pkgdef-and-pkgundef-files"></a>Náhradní řetězce použité v souborech .Pkgdef a .Pkgundef
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete použít náhradní řetězce uvedené níže v souborech. pkgdef a. pkgundef, které definujete pro aplikaci izolovaného prostředí sady Visual Studio.  
  
## <a name="substitution-strings"></a>Náhradní řetězce  
  
|Řetězec|Popis|  
|------------|-----------------|  
|$=*Hledat*$|Hodnota položky *registryentry* Pokud řetězec položky registru končí zpětným lomítkem ( \\ ), je použita výchozí hodnota podklíče registru. Například substituční řetězec $ = HKEY_CURRENT_USER \Environment\TEMP $ se rozšíří na dočasnou složku aktuálního uživatele.|  
|$AppName $|Kvalifikovaný název aplikace, která je předána AppEnv.dll vstupním bodům. Kvalifikovaný název se skládá z názvu aplikace, podtržítka a identifikátoru třídy (CLSID) automatizačního objektu aplikace, který je také zaznamenán jako hodnota nastavení ThisVersionDTECLSID v souboru Project. pkgdef.|  
|$AppDataLocalFolder|Podsložka% LOCALAPPDATA% pro tuto aplikaci.|  
|$BaseInstallDir $|Úplná cesta k umístění, kde je nainstalována aplikace Visual Studio.|  
|$CommonFiles $|Hodnota proměnné prostředí% CommonProgramFiles%.|  
|$MyDocuments $|Úplná cesta ke složce dokumenty aktuálního uživatele.|  
|$PackageFolder $|Úplná cesta k adresáři, který obsahuje soubory sestavení balíčku pro aplikaci.|  
|$ProgramFiles $|Hodnota proměnné prostředí% ProgramFiles%.|  
|$RootFolder $|Úplná cesta ke kořenovému adresáři aplikace.|  
|$RootKey $|Klíč kořenového registru pro aplikaci Ve výchozím nastavení je kořen v HKEY_CURRENT_USER \Software \\ *CompanyName* \\ *ProjectName* \\ *VersionNumber* (Pokud je aplikace spuštěná, _Config je připojen k tomuto klíči). Je nastavená hodnotou RegistryRoot v souboru *řešení*. pkgdef.<br /><br /> $RootKey $ String lze použít k načtení hodnoty registru pod podklíčem aplikace. Například řetězec "$ = $RootKey $ \AppIcon $" vrátí hodnotu položky AppIcon v kořenovém podklíči aplikace.<br /><br /> Analyzátor zpracuje soubor. pkgdef sekvenčně a může získat přístup k položce registru v podklíči aplikace pouze v případě, že položka byla dříve definována.|  
|$ShellFolder $|Úplná cesta k umístění, kde je nainstalována aplikace Visual Studio.|  
|$System $|Složka Windows\System32|  
|$WINDIR $|Složka Windows.|  
  
 Pokud analyzátor nerozpozná náhradní řetězec nebo nemůže určit hodnotu položky registru nebo proměnné prostředí, pak neprovede substituci v této části řetězce.
