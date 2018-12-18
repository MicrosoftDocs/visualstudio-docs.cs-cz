---
title: Registrace operací pro přípony názvů souborů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3a1300f7f66e9c3e9e9cebe3a7b0c7c84e7df4c2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782424"
---
# <a name="registering-verbs-for-file-name-extensions"></a>Registrace operací pro přípony názvů souborů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Přidružení příponu názvu souboru pomocí aplikace je obecně upřednostňované akce, ke které dochází, když uživatel pokliká soubor. To upřednostňovaný akce je spojena se slovesem, například aplikaci, která odpovídá akci.  
  
 Můžete zaregistrovat příkazy, které jsou spojeny s programový identifikátor (ProgID) pro rozšíření s použitím prostředí klíče umístěné na HKEY_CLASSES_ROOT\\*progid*\shell. Další informace najdete v tématu [typy souborů](http://msdn.microsoft.com/library/windows/desktop/cc144148\(v=vs.85\).aspx).  
  
## <a name="registering-standard-verbs"></a>Registruje standardní příkazy  
 Operační systém rozpozná standardní následující příkazy:  
  
- Otevřít  
  
- Upravit  
  
- Přehrát  
  
- Tisk  
  
- Náhled  
  
  Kdykoli je to možné, zaregistrujte standardní příkaz. Nejběžnější je sloveso otevřít. Použijte příkaz upravit jenom v případě, že je vymazat rozdíl mezi otevřením souboru a úpravy souboru. Například otevřete soubor HTM jej zobrazí v prohlížeči, že úpravy něho soubor .htm spuštění editoru HTML. Standardní příkazy jsou lokalizovány s národním prostředím operačního systému.  
  
> [!NOTE]
>  Při registraci standardní příkazy, nenastavujte výchozí hodnotu pro klíč otevřete. Výchozí hodnota obsahuje řetězec zobrazení v nabídce. Operační systém poskytuje tento řetězec pro standardní příkazy.  
  
 Soubory projektu by měly být zaregistrovány spustit novou instanci třídy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] když uživatel otevře soubor. Následující příklad ukazuje standardní příkaz registrace [!INCLUDE[csprcs](../includes/csprcs-md.md)] projektu.  
  
```  
[HKEY_CLASSES_ROOT\.csproj]  
@="VisualStudio.csproj.8.0"  
  
[HKEY_CLASSES_ROOT\.csproj\OpenWithList]  
[HKEY_CLASSES_ROOT\.csproj\OpenWithList\VSLauncher.exe]  
@=""  
  
[HKEY_CLASSES_ROOT\.csproj\OpenWithProgids]  
"VisualStudio.csproj.8.0"=""  
  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open\Command]  
@="C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe \"%1\""  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0]  
@="C# Project file"  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\DefaultIcon]  
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,0"  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell]  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open]  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open\Command]  
@="\"C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe\" \"%1\""  
```  
  
 Pro otevření souboru v existující instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], zaregistrujte DDEEXEC klíč. Následující příklad ukazuje standardní příkaz registrace [!INCLUDE[csprcs](../includes/csprcs-md.md)] .cs souboru.  
  
```  
[HKEY_CLASSES_ROOT\.cs]  
@="VisualStudio.cs.8.0"  
  
[HKEY_CLASSES_ROOT\.cs\OpenWithList]  
[HKEY_CLASSES_ROOT\.cs\OpenWithList\devenv.exe]  
@=""  
  
[HKEY_CLASSES_ROOT\.cs\OpenWithProgids]  
"VisualStudio.cs.8.0"=""  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0]  
@="C# Source file"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\DefaultIcon]  
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,1"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell]  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open]  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\Command]  
@="\"C:\\VisualStudioPath\\Common7\\IDE\\devenv.exe\" /dde \"%1\""  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec]  
@="Open(\"%1\")"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Application]  
@="VisualStudio.8.0"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Topic]  
@="system"  
```  
  
## <a name="setting-the-default-verb"></a>Nastavení výchozí příkaz  
 Je příkaz výchozí akci, která se spustí v případě, že uživatel dvakrát klikne soubor v Průzkumníku Windows. Výchozí příkaz je jako výchozí hodnota zadaná pro HKEY_CLASSES_ROOT operace\\*progid*\Shell klíč. Pokud není zadána žádná hodnota, výchozí příkaz je zadaná v HKEY_CLASSES_ROOT první operace\\*progid*\Shell seznam klíčů.  
  
> [!NOTE]
>  Pokud chcete změnit výchozí příkaz rozšíření v nasazení vedle sebe, zvažte dopad na instalaci a odebrání. Během instalace se přepíše původní výchozí hodnotu.  
  
## <a name="see-also"></a>Viz také  
 [Správa přidružení souborů vedle sebe](../extensibility/managing-side-by-side-file-associations.md)

