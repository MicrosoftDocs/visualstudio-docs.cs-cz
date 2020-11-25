---
title: Přidání hlavičky souboru
description: Naučte se používat soubor EditorConfig k přidávání hlaviček souborů do existujících souborů, projektů a řešení.
ms.custom: SEO-VS-2020
ms.date: 07/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5f2e4715c0333b02f120ec5f92d9f742196c04f3
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/25/2020
ms.locfileid: "95870856"
---
# <a name="add-file-header"></a>Přidání hlavičky souboru

Tato generace kódu platí pro:

- C#

- Visual Basic

**Co:** Do existujících souborů, projektů a řešení můžete přidat záhlaví souborů pomocí [EditorConfig](../create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

**Když:** Chcete snadno přidat záhlaví souboru do souborů, projektů a řešení.

**Proč:** Váš tým vyžaduje, abyste zahrnuli hlavičku souboru pro účely autorského práva. 

## <a name="how-to"></a>Postupy

1. Přidejte [EditorConfig](../create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project) do projektu nebo řešení, pokud ho ještě nemáte.

2. Do souboru EditorConfig přidejte následující pravidlo: *file_header_template*.

3. Nastavte hodnotu pravidla tak, aby se rovnala textu záhlaví, který chcete použít. Můžete použít `{fileName}` jako zástupný symbol pro název souboru.

    ![Snímek obrazovky se souborem EditorConfig zobrazujícím hodnotu file_header_template](media/add-file-header-rule.png)

    > [!NOTE]
    > V EditorConfig nemůžete mít explicitní víceřádkové řádky a k vložení nových řádků bude potřeba použít znak nového řádku UNIX.

4. Umístěte blikající kurzor na první řádek jakéhokoli souboru C# nebo Visual Basic.

5. Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .

6. Vyberte možnost **Přidat hlavičku souboru**. 

    ![Snímek obrazovky s možností záhlaví přidat soubor](media/add-file-header.png)

7. Chcete-li použít hlavičku souboru na celý projekt nebo řešení, vyberte možnost **projekt** nebo **řešení** pod možností **opravit všechny výskyty v:** .

8. Otevře se dialogové okno **opravit všechny výskyty** , kde můžete zobrazit náhled změn.

    ![Dialog opravit všechny výskyty](media/file-header-preview-changes.png)

8. Chcete-li změny použít, vyberte **použít** .

## <a name="see-also"></a>Viz také

- [Generování kódu](../code-generation-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)