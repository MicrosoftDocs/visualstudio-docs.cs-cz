---
title: Alias – příkaz
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 41bddec00866f7c10140abc40c5ff12c623310d3
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33703393"
---
# <a name="alias-command"></a>Alias – příkaz
Vytvoří nový alias pro dokončení příkazu, úplný příkaz i jeho argumenty nebo jiný alias.

> [!TIP]
> Zadáním `>alias` bez argumentů zobrazí aktuální seznam aliasů a jejich definice.


## <a name="syntax"></a>Syntaxe

```cmd
Tools.Alias [/delete] [/reset] [aliasname] [aliasstring]
```

## <a name="arguments"></a>Arguments
 `aliasname` Volitelný parametr. Název pro nový alias. Pokud je zadána žádná hodnota pro `aliasname`, zobrazí se seznam aktuální aliasy a jejich definice.

 `aliasstring` Volitelný parametr. Název dokončení příkazu nebo existující alias a všechny parametry, které chcete vytvořit jako alias. Pokud je zadána žádná hodnota pro `aliasstring`, název aliasu a alias řetězec pro zadaný alias zobrazí.

## <a name="switches"></a>Přepínače
 / DELETE nebo/del nebo /d volitelné. Odstraní zadaný alias a odebere ji z automatické dokončování.

 / reset volitelné. Seznam předdefinovaných aliasy obnoví původní nastavení. To znamená obnoví všechny předdefinované aliasy a odebere všechny aliasy definovaný uživatelem.

## <a name="remarks"></a>Poznámky
 Vzhledem k tomu, že aliasy představují příkazy, musí být umístěna na začátek příkazového řádku.

 Při vystavování tento příkaz, přepínače by měla obsahovat ihned po příkazu není po aliasy, v opačném případě bude součástí řetězec aliasu přepínač sám sebe.

 `/reset` Přepínač požádá o potvrzení před zástupci jsou obnoveny. Neexistuje žádné zkratka pro `/reset`.

## <a name="examples"></a>Příklady
 Tento příklad vytvoří nový alias `upper`, pro kompletní příkaz Edit.MakeUpperCase.

```cmd
>Tools.Alias upper Edit.MakeUpperCase
```

 Tento příklad odstraní alias, `upper`.

```cmd
>Tools.alias /delete upper
```

 Tento příklad zobrazí seznam všech aktuální aliasy a definice.

```cmd
>Tools.Alias
```

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole najít/příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)