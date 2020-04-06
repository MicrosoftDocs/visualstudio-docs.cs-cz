---
title: Otevírání a ukládání položek projektu | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706968"
---
# <a name="opening-and-saving-project-items"></a>Otevření a uložení položek projektu
Přidáte-li nový typ projektu, je nutné spravovat otevírání a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ukládání souborů projektů v integrovaném vývojovém prostředí (IDE). Následující témata popisují různé přístupy k otevírání a ukládání souborů.

## <a name="in-this-section"></a>V tomto oddílu
- [Zobrazení souborů pomocí příkazu Otevřít soubor](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)

 Poskytuje podrobné vysvětlení, jak ide zpracovává příkaz **Otevřít soubor** a roli projektů v reakci na tento příkaz.

- [Zobrazení souborů pomocí příkazu Otevřít v aplikaci](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)

 Poskytuje podrobné podrobné vysvětlení, jak rozhraní IDE zpracovává příkaz **Otevřít s,** což vyzve k otevření souboru, který má určitý výběr standardních editorů.

- [Postupy: Otevření editoru pro konkrétní projekt](../../extensibility/how-to-open-project-specific-editors.md)

 Obsahuje podrobné pokyny pro určení, že soubory určitého typu v projektu by měly být otevřeny pomocí editoru specifického pro projekt.

- [Postupy: Otevření standardních editorů](../../extensibility/how-to-open-standard-editors.md)

 Obsahuje podrobné pokyny pro určení, jak povolit rozhraní IDE otevřít standardní editor pro soubory v typu projektu.

- [Postupy: Otevření editorů pro otevřené dokumenty](../../extensibility/how-to-open-editors-for-open-documents.md)

 Obsahuje podrobné pokyny k otevření editoru specifického pro projekt pro otevřený soubor.

- [Uložení standardního dokumentu](../../extensibility/internals/saving-a-standard-document.md)

 Poskytuje podrobné vysvětlení, jak rozhraní IDE zpracovává příkazy **Uložit**, **Uložit jako**a **Uložit vše** pro dokument otevřený ve standardním editoru.

- [Uložení vlastního dokumentu](../../extensibility/internals/saving-a-custom-document.md)

 Poskytuje diagram a podrobné vysvětlení, jak rozhraní IDE zpracovává příkazy **Uložit**, **Uložit jako**a **Uložit všechny** pro dokumenty otevřené ve vlastním editoru.

- [Určení editoru, který otevře soubor v projektu](../../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)

 Popisuje proces, který sleduje rozhraní IDE a vybere příslušný editor nebo návrhář e-souboru.

## <a name="related-sections"></a>Související oddíly
- [Vytváření vlastních editorů a návrhářů](../../extensibility/creating-custom-editors-and-designers.md)

 Uvádí čtyři typy editorů, které může ide hostovat a poskytuje popisy každého editoru.

- [Typy projektů](../../extensibility/internals/project-types.md)

 Popisuje, jak projekty řídí způsob, jakým je kód kompilován a sestaven, jak jsou otevřeny editory a jak jsou formátovány položky projektu.
