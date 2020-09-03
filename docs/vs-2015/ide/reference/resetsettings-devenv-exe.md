---
title: -ResetSettings (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 41e402a9268acecb70c83e26bab0e682d4ec59f5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665586"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Obnoví [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] výchozí nastavení a automaticky spustí [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrované vývojové prostředí (IDE). Volitelně obnoví nastavení na zadaný soubor. vssettings.

 Výchozí nastavení jsou určena profilem, který byl vybrán při [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] prvním spuštění.

## <a name="syntax"></a>Syntaxe

```
Devenv /ResetSettings SettingsFile
```

## <a name="arguments"></a>Argumenty
 `SettingsFile` Úplná cesta a název souboru. vssettings, který se má použít pro [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .

 K obnovení profilu obecného nastavení vývoje použijte `General` .

## <a name="remarks"></a>Poznámky
 Pokud `SettingsFile` není zadán, zobrazí se výzva k výběru výchozí kolekce nastavení při příštím spuštění [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .

## <a name="example"></a>Příklad
 Následující příkazový řádek použije nastavení uložená v souboru `MySettings.vssettings` .

```
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"
```

## <a name="see-also"></a>Viz také
 [Přizpůsobení nastavení vývoje v](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) [přepínačích příkazového řádku devenv](../../ide/reference/devenv-command-line-switches.md) sady Visual Studio
