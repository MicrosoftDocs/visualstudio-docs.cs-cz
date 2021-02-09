---
title: Připojovací řetězec obsahuje heslo.
description: Připojovací řetězec obsahuje přihlašovací údaje s heslem uloženým jako nešifrovaný text a nevyužívá integrované zabezpečení.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 1ce11b59ad7f38de4c71fa13371da16225b5b843
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858407"
---
# <a name="the-connection-string-contains-credentials-with-a-clear-text-password-and-is-not-using-integrated-security"></a>Připojovací řetězec obsahuje přihlašovací údaje s heslem uloženým jako nešifrovaný text a nevyužívá integrované zabezpečení.

Chcete uložit připojovací řetězec do aktuálního souboru DBML a konfiguračních souborů aplikace s těmito citlivými informacemi?  Kliknutím na **ne** uložte připojovací řetězec bez citlivých informací.

Při práci s datovými připojeními, která obsahují citlivé informace (hesla, která jsou obsažena v připojovacím řetězci), máte možnost Uložit připojovací řetězec do souboru DBML a konfiguračního souboru aplikace v projektu s nebo bez citlivých informací.

> [!WARNING]
> Explicitním nastavením vlastnosti **připojení** vlastnost **nastavení aplikace** na **hodnotu NEPRAVDA** přidá heslo do souboru DBML.

## <a name="save-options"></a>Možnosti uložení

- Pokud chcete uložit připojovací řetězec s citlivými informacemi, klikněte na **Ano**.

   Připojovací řetězec je uložen jako nastavení aplikace. Připojovací řetězec obsahuje citlivé informace v prostém textu. Soubor DBML neobsahuje citlivé informace.

- Pokud chcete uložit připojovací řetězec bez citlivých informací, klikněte na tlačítko **ne**.

   Připojovací řetězec je uložen jako nastavení aplikace, ale heslo není zahrnuto.

## <a name="see-also"></a>Viz také

- [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
