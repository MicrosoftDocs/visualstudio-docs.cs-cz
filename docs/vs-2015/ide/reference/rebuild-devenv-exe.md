---
title: -Opětovné sestavení (devenv.exe) | Dokumentace Microsoftu
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
- Devenv, /rebuild switch
- rebuild Devenv switch (/rebuild)
- projects [Visual Studio], rebuilding
- /rebuild Devenv switch
- applications [Visual Studio], rebuilding
ms.assetid: c5a8a4bf-0e2b-46eb-a44a-8aeb29b92c32
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 58cd259f602d1f2364b37d8d6905753b2ce44068
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49285763"
---
# <a name="rebuild-devenvexe"></a>/Rebuild (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Čistí a poté sestaví Zadaná konfigurace řešení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
devenv SolutionName /rebuild SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]  
```  
  
## <a name="arguments"></a>Arguments  
 `SolnConfigName`  
 Požadováno. Název konfigurace řešení, která se použije k opětovnému sestavení řešení s názvem v `SolutionName`.  
  
 `SolutionName`  
 Požadováno. Úplná cesta a název souboru řešení.  
  
 / Project `ProjName`  
 Volitelné. Cesta a název souboru projektu v rámci řešení. Můžete zadat relativní cestu z `SolutionName` složku do souboru projektu nebo zobrazované jméno projektu, nebo úplnou cestu a název souboru projektu.  
  
 / projectconfig `ProjConfigName`  
 Volitelné. Název projektu konfigurace se použije při opětovném sestavování sestavení `/project` s názvem.  
  
## <a name="remarks"></a>Poznámky  
  
-   Tento přepínač provádí stejnou funkci jako **znovu sestavit řešení** příkazu nabídky v rámci integrovaného vývojového prostředí (IDE).  
  
-   Uzavření řetězců, které obsahují mezery v dvojitých uvozovkách.  
  
-   Souhrnné informace o vyčistí a sestavení, včetně chyb, mohou být zobrazeny v **příkaz** okna, nebo do jakéhokoli souboru protokolu zadaný `/out` přepnout.  
  
## <a name="example"></a>Příklad  
 Tento příklad odstraní a znovu sestaví projekt `CSharpWinApp`, použije `Debug` konfigurace sestavení projektu v rámci `Debug` konfigurace řešení `MySolution`.  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /rebuild Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## <a name="see-also"></a>Viz také  
 [Přepínače příkazového řádku nástroje devenv](../../ide/reference/devenv-command-line-switches.md)   
 [/ Sestavení (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/ Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)   
 [/ Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)



