---
title: Příkaz alias | Dokumentace Microsoftu
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
- tools.alias
helpviewer_keywords:
- aliases, Visual Studio commands
- commands, aliases
- Tools.Alias command
- command aliases
- alias command
ms.assetid: bdf857df-b5d5-450f-8c10-a6fd4dccc130
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f9fb6a4da0b18cf022ee388ff4a6fa5f399dc650
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49258515"
---
# <a name="alias-command"></a>Alias – příkaz
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Vytvoří nový alias pro úplný příkaz, úplný příkaz a argumenty, nebo jiný alias.  
  
> [!TIP]
>  Zadáním `>alias` bez argumentů zobrazí aktuální seznam aliasů a jejich definice.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Tools.Alias [/delete] [/reset] [aliasname] [aliasstring]  
```  
  
## <a name="arguments"></a>Arguments  
 `aliasname`  
 Volitelné. Název pro nový alias. Pokud není zadána žádná hodnota pro `aliasname`, zobrazí se seznam aktuálních aliasů a jejich definice.  
  
 `aliasstring`  
 Volitelné. Úplný název příkazu nebo existující alias a všechny parametry, které chcete vytvořit jako alias. Pokud není zadána žádná hodnota pro `aliasstring`, název aliasu a řetězec aliasu pro zadaný alias se zobrazí.  
  
## <a name="switches"></a>Přepínače  
 / DELETE nebo/del nebo /d  
 Volitelné. Odstraní určený alias a odebere ji z automatického dokončování.  
  
 / Reset  
 Volitelné. Obnoví původní nastavení seznamu předdefinovaných aliasů. To znamená, že obnoví všechny předdefinované aliasy a odebere všechny aliasy definované uživatelem.  
  
## <a name="remarks"></a>Poznámky  
 Vzhledem k tomu, že aliasy představují příkazy, musí být umístěné na začátku příkazového řádku.  
  
 Při vydávání tohoto příkazu byste měli zahrnout přepínače bezprostředně za příkaz, nikoli za aliasy, jinak bude přepínač samotný součástí řetězce aliasu.  
  
 `/reset` Přepínač žádá o potvrzení před aliasů. Neexistuje krátký tvar `/reset`.  
  
## <a name="examples"></a>Příklady  
 Tento příklad vytvoří nový alias `upper`, pro kompletní příkaz Edit.MakeUpperCase.  
  
```  
>Tools.Alias upper Edit.MakeUpperCase  
```  
  
 Tento příklad odstraní alias, `upper`.  
  
```  
>Tools.alias /delete upper  
```  
  
 Tento příklad zobrazuje seznam všech aktuálních aliasů a definic.  
  
```  
>Tools.Alias  
```  
  
## <a name="see-also"></a>Viz také  
 [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Okno příkazového řádku](../../ide/reference/command-window.md)   
 [Pole najít/příkaz](../../ide/find-command-box.md)   
 [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



