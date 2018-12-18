---
title: Příkaz Přidat existující projekt | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c881f32594ee6327dfba9792fa83bd2d092efcf9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49267641"
---
# <a name="add-existing-project-command"></a>Přidat existující projekt – příkaz
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Přidá existující projekt do aktuálního řešení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
File.AddExistingProject filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Volitelné. Úplnou cestu a projekt název, pomocí rozšíření projektu pro přidání do řešení.  
  
 Pokud `filename` argument obsahuje mezery, musí být uzavřen v uvozovkách.  
  
 Pokud není zadán žádný název souboru, bude příkaz tak, že tento uživatel může vybrat projekt otevřete dialogové okno souboru.  
  
## <a name="remarks"></a>Poznámky  
 Automatické dokončování, pokusí se najít správnou cestu a název souboru během psaní.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu přidá [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] projektu, projekt testproject1 vyžaduje, do aktuálního řešení.  
  
```  
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"  
```  
  
## <a name="see-also"></a>Viz také  
 [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Okno příkazového řádku](../../ide/reference/command-window.md)   
 [Pole najít/příkaz](../../ide/find-command-box.md)   
 [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



