---
title: Alias – příkaz
ms.date: 11/04/2016
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 031f1a4bab1acee3f3d0999b17c0b607f7808df9
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596902"
---
# <a name="alias-command"></a>Alias – příkaz
Vytvoří nový alias pro úplný příkaz, úplný příkaz a argumenty nebo jiný alias.

> [!TIP]
> Zadáním `>alias` bez argumentů se zobrazí aktuální seznam aliasů a jejich definice.

## <a name="syntax"></a>Syntaxe

```cmd
Tools.Alias [/delete] [/reset] [aliasname] [aliasstring]
```

## <a name="arguments"></a>Arguments
`aliasname`\
Volitelné. Název nového aliasu Pokud není zadána žádná hodnota pro `aliasname`, zobrazí se seznam aktuálních aliasů a jejich definice.

`aliasstring`\
Volitelné. Úplný název příkazu nebo existující alias a všechny parametry, které chcete vytvořit jako alias. Pokud není zadána žádná hodnota pro `aliasstring`, zobrazí se název aliasu a řetězec aliasu pro zadaný alias.

## <a name="switches"></a>Přepínače
/Delete nebo/del nebo/D\
Volitelné. Odstraní zadaný alias a odebere ho z automatického dokončování.

/Reset po vyčištění\
Volitelné. Obnoví původní nastavení seznamu předem definovaných aliasů. To znamená, že obnoví všechny předdefinované aliasy a odstraní všechny aliasy definované uživatelem.

## <a name="remarks"></a>Poznámky
Vzhledem k tomu, že aliasy představují příkazy, musí být umístěny na začátku příkazového řádku.

Při vydávání tohoto příkazu byste měli zahrnout přepínače hned za příkaz, nikoli za aliasy, jinak bude samotný přepínač zahrnut jako součást řetězce aliasu.

Přepínač `/reset` před obnovením aliasů vyžádá o potvrzení. Neexistuje žádná krátká forma `/reset`.

## <a name="examples"></a>Příklady
Tento příklad vytvoří nový alias, `upper`pro příkaz Complete. MakeUpperCase.

```cmd
>Tools.Alias upper Edit.MakeUpperCase
```

Tento příklad odstraní alias `upper`.

```cmd
>Tools.alias /delete upper
```

Tento příklad zobrazuje seznam všech aktuálních aliasů a definic.

```cmd
>Tools.Alias
```

## <a name="see-also"></a>Viz také:

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole Najít/příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
