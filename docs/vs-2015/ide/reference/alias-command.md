---
title: Alias – příkaz | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6da744b0db9e41cd1e5039a1bd0d5c93bc4c734a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651694"
---
# <a name="alias-command"></a>Alias – příkaz
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vytvoří nový alias pro úplný příkaz, úplný příkaz a argumenty nebo jiný alias.

> [!TIP]
> Zadáním `>alias` bez argumentů se zobrazí aktuální seznam aliasů a jejich definice.

## <a name="syntax"></a>Syntaxe

```
Tools.Alias [/delete] [/reset] [aliasname] [aliasstring]
```

## <a name="arguments"></a>Arguments
 `aliasname` volitelné. Název nového aliasu Pokud není zadána žádná hodnota pro `aliasname`, zobrazí se seznam aktuálních aliasů a jejich definice.

 `aliasstring` volitelné. Úplný název příkazu nebo existující alias a všechny parametry, které chcete vytvořit jako alias. Pokud není zadána žádná hodnota pro `aliasstring`, zobrazí se název aliasu a řetězec aliasu pro zadaný alias.

## <a name="switches"></a>Přepínače
 /Delete nebo/del nebo/d volitelné. Odstraní zadaný alias a odebere ho z automatického dokončování.

 /Reset po vyčištění je nepovinný. Obnoví původní nastavení seznamu předem definovaných aliasů. To znamená, že obnoví všechny předdefinované aliasy a odstraní všechny aliasy definované uživatelem.

## <a name="remarks"></a>Poznámky
 Vzhledem k tomu, že aliasy představují příkazy, musí být umístěny na začátku příkazového řádku.

 Při vydávání tohoto příkazu byste měli zahrnout přepínače hned za příkaz, nikoli za aliasy, jinak bude samotný přepínač zahrnut jako součást řetězce aliasu.

 Přepínač `/reset` před obnovením aliasů vyžádá o potvrzení. Neexistuje žádná krátká forma `/reset`.

## <a name="examples"></a>Příklady
 Tento příklad vytvoří nový alias, `upper` pro příkaz Complete. MakeUpperCase.

```
>Tools.Alias upper Edit.MakeUpperCase
```

 Tento příklad odstraní alias `upper`.

```
>Tools.alias /delete upper
```

 Tento příklad zobrazuje seznam všech aktuálních aliasů a definic.

```
>Tools.Alias
```

## <a name="see-also"></a>Viz také
 [Příkazy](../../ide/reference/visual-studio-commands.md) [příkazového](../../ide/reference/command-window.md) řádku [find/Command](../../ide/find-command-box.md) v příkazu Visual Studio Command a Command [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
