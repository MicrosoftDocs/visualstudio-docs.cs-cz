---
title: Otevírání a ukládání položek projektu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], file persistence
- files [Visual Studio], opening and saving
- editors [Visual Studio SDK], file persistence
ms.assetid: f71898ad-335f-4c43-a177-4da87078afd1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbb89d99e401be6bae7d8ee9be8ee33fa7574723
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706968"
---
# <a name="opening-and-saving-project-items"></a>Otevření a uložení položek projektu
Když přidáte nový typ projektu, musíte spravovat otevírání a ukládání souborů projektů v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrovaném vývojovém prostředí (IDE). Následující témata popisují různé přístupy k otevírání a ukládání souborů.

## <a name="in-this-section"></a>V tomto oddílu
- [Zobrazení souborů pomocí příkazu Otevřít soubor](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)

 Poskytuje podrobné vysvětlení způsobu, jakým rozhraní IDE zpracovává příkaz pro **otevření souboru** a role projektů v reakci na tento příkaz.

- [Zobrazení souborů pomocí příkazu Otevřít v aplikaci](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)

 Obsahuje podrobné vysvětlení způsobu, jakým rozhraní IDE zpracuje příkaz **otevřít pomocí** , a zobrazí výzvu k otevření souboru, který má několik možností standardního editoru.

- [Postupy: Otevření editoru pro konkrétní projekt](../../extensibility/how-to-open-project-specific-editors.md)

 Poskytuje podrobné pokyny pro určení, že soubory určitého typu v projektu by měly být otevřeny pomocí editoru specifického pro projekt.

- [Postupy: Otevření standardních editorů](../../extensibility/how-to-open-standard-editors.md)

 Poskytuje podrobné pokyny pro určení způsobu povolení rozhraní IDE pro otevření standardního editoru souborů v typu projektu.

- [Postupy: Otevření editorů pro otevřené dokumenty](../../extensibility/how-to-open-editors-for-open-documents.md)

 Poskytuje podrobné pokyny pro otevření editoru specifického pro projekt pro otevřený soubor.

- [Uložení standardního dokumentu](../../extensibility/internals/saving-a-standard-document.md)

 Poskytuje podrobné vysvětlení způsobu, jakým rozhraní IDE zpracovává příkazy **Uložit**, **Uložit jako**a **Uložit všechny** příkazy pro dokument otevřený ve standardním editoru.

- [Uložení vlastního dokumentu](../../extensibility/internals/saving-a-custom-document.md)

 Poskytuje diagram a podrobné vysvětlení způsobu, jakým integrované vývojové prostředí (IDE) zpracovává **ukládání**, **ukládání**a **ukládání všech** příkazů pro dokumenty otevřené ve vlastním editoru.

- [Určení editoru, který otevře soubor v projektu](../../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)

 Popisuje proces, který IDE následuje k výběru vhodného editoru nebo návrháře pro soubor.

## <a name="related-sections"></a>Související oddíly
- [Vytváření vlastních editorů a návrhářů](../../extensibility/creating-custom-editors-and-designers.md)

 Uvádí čtyři typy editorů, které může IDE hostovat, a poskytuje popisy jednotlivých editorů.

- [Typy projektů](../../extensibility/internals/project-types.md)

 Popisuje, jak projekty řídí způsob kompilování a sestavení kódu, jak jsou otevřeny editory a jak jsou formátovány položky projektu.
