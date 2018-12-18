---
title: -ResetSettings (devenv.exe) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 276205ae2aab3c38ceb3d4f1419e0bac13ae626c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49273491"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Obnoví [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] výchozí nastavení a automaticky spouští [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrovaného vývojového prostředí. Volitelně obnoví nastavení zadaného souboru .vssettings.  
  
 Výchozí nastavení jsou určena podle profilu, který byl vybrán při [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] prvním spuštění.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Devenv /ResetSettings SettingsFile  
```  
  
## <a name="arguments"></a>Arguments  
 `SettingsFile`  
 Úplná cesta a název souboru .vssettings vyrovnat [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 K obnovení profilu Obecné vývojové nastavení použijte `General`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud ne `SettingsFile` není zadán, zobrazí se výzva k výběru výchozí kolekce nastavení při příštím spuštění [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="example"></a>Příklad  
 Následující příkazový řádek použije nastavení uložená v souboru `MySettings.vssettings`.  
  
```  
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"  
```  
  
## <a name="see-also"></a>Viz také  
 [Přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md)



