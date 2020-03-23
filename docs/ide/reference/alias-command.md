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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596902"
---
# <a name="alias-command"></a>Alias – příkaz
Vytvoří nový alias pro úplný příkaz, úplný příkaz a argumenty nebo jiný alias.

> [!TIP]
> Při `>alias` psaní bez argumentů se zobrazí aktuální seznam aliasů a jejich definice.

## <a name="syntax"></a>Syntaxe

```cmd
Tools.Alias [/delete] [/reset] [aliasname] [aliasstring]
```

## <a name="arguments"></a>Argumenty
`aliasname`\
Nepovinný parametr. Název nového aliasu. Pokud pro `aliasname`ně není zadána žádná hodnota , zobrazí se seznam aktuálních aliasů a jejich definice.

`aliasstring`\
Nepovinný parametr. Úplný název příkazu nebo existující alias a všechny parametry, které chcete vytvořit jako alias. Pokud pro `aliasstring`ně není zadána žádná hodnota , zobrazí se název aliasu a řetězec aliasu pro zadaný alias.

## <a name="switches"></a>Přepínače
/delete nebo /del nebo /d\
Nepovinný parametr. Odstraní zadaný alias a odstraní jej z automatického dokončování.

/reset\
Nepovinný parametr. Obnoví původní nastavení seznamu předdefinovaných aliasů. To znamená, že obnoví všechny předdefinované aliasy a odebere všechny uživatelem definované aliasy.

## <a name="remarks"></a>Poznámky
Vzhledem k tomu, že aliasy představují příkazy, musí být umístěny na začátku příkazového řádku.

Při vydávání tohoto příkazu byste měli zahrnout přepínače ihned za příkaz, nikoli za aliasy, jinak bude samotný přepínač zahrnut jako součást řetězce aliasu.

Přepínač `/reset` požádá o potvrzení před obnovením aliasů. Neexistuje žádná krátká `/reset`forma .

## <a name="examples"></a>Příklady
Tento příklad vytvoří nový `upper`alias , pro úplný příkaz Edit.MakeUpperCase.

```cmd
>Tools.Alias upper Edit.MakeUpperCase
```

Tento příklad odstraní alias `upper`.

```cmd
>Tools.alias /delete upper
```

V tomto příkladu se zobrazí seznam všech aktuálních aliasů a definic.

```cmd
>Tools.Alias
```

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Najít/Příkazové pole](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
