---
title: Alias – příkaz
description: Naučte se, jak pomocí příkazu alias vytvořit nový alias pro úplný příkaz, úplný příkaz a argumenty nebo jiný alias.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7a20a14cc0f48e86840b770aca934b188bf152dd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969786"
---
# <a name="alias-command"></a>Alias – příkaz
Vytvoří nový alias pro úplný příkaz, úplný příkaz a argumenty nebo jiný alias.

> [!TIP]
> `>alias`Při psaní bez argumentů se zobrazí aktuální seznam aliasů a jejich definice.

## <a name="syntax"></a>Syntaxe

```cmd
Tools.Alias [/delete] [/reset] [aliasname] [aliasstring]
```

## <a name="arguments"></a>Argumenty
`aliasname`\
Nepovinný parametr. Název nového aliasu Pokud není zadána žádná hodnota pro `aliasname` , zobrazí se seznam aktuálních aliasů a jejich definice.

`aliasstring`\
Nepovinný parametr. Úplný název příkazu nebo existující alias a všechny parametry, které chcete vytvořit jako alias. Pokud není zadána žádná hodnota pro `aliasstring` , zobrazí se název aliasu a řetězec aliasu pro zadaný alias.

## <a name="switches"></a>přepínače,
/Delete nebo/del nebo/D\
Nepovinný parametr. Odstraní zadaný alias a odebere ho z automatického dokončování.

/Reset po vyčištění
Nepovinný parametr. Obnoví původní nastavení seznamu předem definovaných aliasů. To znamená, že obnoví všechny předdefinované aliasy a odstraní všechny aliasy definované uživatelem.

## <a name="remarks"></a>Poznámky
Vzhledem k tomu, že aliasy představují příkazy, musí být umístěny na začátku příkazového řádku.

Při vydávání tohoto příkazu byste měli zahrnout přepínače hned za příkaz, nikoli za aliasy, jinak bude samotný přepínač zahrnut jako součást řetězce aliasu.

`/reset`Přepínač požádá o potvrzení před obnovením aliasů. Neexistuje žádná krátká forma `/reset` .

## <a name="examples"></a>Příklady
Tento příklad vytvoří nový alias, `upper` pro kompletní příkaz Edit. MakeUpperCase.

```cmd
>Tools.Alias upper Edit.MakeUpperCase
```

Tento příklad odstraní alias, `upper` .

```cmd
>Tools.alias /delete upper
```

Tento příklad zobrazuje seznam všech aktuálních aliasů a definic.

```cmd
>Tools.Alias
```

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole Najít/příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
