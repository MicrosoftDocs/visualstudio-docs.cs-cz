---
title: 'Možnosti, textový editor, F #, opravy kódu'
description: 'Naučte se, jak pomocí stránky opravy kódu v oddílu F # určit nastavení, které může pomáhat identifikovat chyby kódu a nabízet řešení.'
ms.custom: SEO-VS-2020
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.F%2523.Code_Fixes
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: ca1b3816786ab611af8acb1cb99eea406ca6ad45
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943949"
---
# <a name="options-text-editor--f--code-fixes"></a>Možnosti: textový editor > F # > opravy kódu

Pomocí stránky možnosti oprav kódu můžete určit nastavení, které může pomáhat identifikovat chyby kódu a nabízet řešení. Chcete-li získat přístup k této stránce Možnosti, zvolte  >  **možnost** nástroje a pak zvolte **textový editor**  >  **F #**  >  **opravy kódu**.

## <a name="code-fixes"></a>Opravy kódu

- **Zjednodušit názvy (odebrat nepotřebné kvalifikátory)**

  Pokud je toto políčko zaškrtnuté, plně kvalifikované názvy budou zjednodušeny, pokud není potřebná kvalifikace, například pro člena často používaného oboru názvů.

- **Vždy umístit otevřené příkazy na nejvyšší úroveň**

  Pokud je toto políčko zaškrtnuté a zadáte `open` příkaz v kódu, je umístěn na nejvyšší úrovni.

- **Odebrat nepoužívané otevřené příkazy**

  Pokud je toto políčko zaškrtnuté, dokumenty se analyzují pro nepoužité `open` příkazy a v [rychlé akci](../quick-actions.md) se zobrazí akce, která odebere všechny nepoužité `open` příkazy.

- **Analyzovat a navrhovat opravy pro nepoužívané hodnoty**

  Pokud je toto zaškrtávací políčko zaškrtnuto, nástroj rozpozná hodnotu, která není v kódu použita. Pokud pak najedete na nepoužitou hodnotu, doporučí se způsob, jakým můžete použít hodnotu.

## <a name="see-also"></a>Viz také

- [Obecné, prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md)
- [Nalezení změn kódu a další historie pomocí CodeLensu](../../ide/find-code-changes-and-other-history-with-codelens.md)
