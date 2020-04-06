---
title: Model služby staršího jazyka | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f024a02641902843f673ce3ff8583a4bce3b135
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707038"
---
# <a name="model-of-a-legacy-language-service"></a>Model služby starší verze jazyka
Jazyková služba definuje prvky a funkce pro konkrétní jazyk a slouží k poskytování informací specifických pro daný jazyk editoru. Editor například potřebuje znát prvky a klíčová slova jazyka, aby podpořil zbarvení syntaxe.

 Služba jazyka úzce spolupracuje s textovou vyrovnávací pamětí spravovanou editorem a zobrazením, které editor obsahuje. Příkladem funkce poskytované jazykovou službou je možnost Microsoft IntelliSense **Quick Info.**

## <a name="a-minimal-language-service"></a>Minimální jazyková služba
 Nejzákladnější jazyková služba obsahuje následující dva objekty:

- *Služba jazyka* implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> rozhraní. Jazyková služba obsahuje informace o jazyce, včetně jeho názvu, rozšíření názvů souborů, správce okna kódu a colorizátoru.

- *Colorizer* implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> rozhraní.

  Následující koncepční výkres ukazuje model základní jazykové služby.

  ![Grafický model služby jazyka](../../extensibility/media/vslanguageservicemodel.gif "vsSLanguageServiceModel") Základní model jazykových služeb

  Okno dokumentu je hostitelem *zobrazení dokumentu* editoru, v tomto případě základní editor. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Zobrazení dokumentu a vyrovnávací paměť textu jsou vlastněny editorem. Tyto objekty [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pracují s prostřednictvím okna specializovaného dokumentu s názvem *okno kódu*. Okno kódu je obsaženo <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> v objektu, který je vytvořen a řízen ide.

  Při načtení souboru s danou příponou editor vyhledá jazykovou službu přidruženou k <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> této příponě a předá mu okno kódu voláním metody. Služba jazyka vrátí *správce okna kódu*, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> který implementuje rozhraní.

  Následující tabulka obsahuje přehled objektů v modelu.

| Komponenta | Objekt | Funkce |
|------------------| - | - |
| Textová vyrovnávací paměť | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> | Datový proud textu pro čtení a zápis unicode. Je možné, že text použít jiné kódování. |
| Okno Kód | <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> | Okno dokumentu, které obsahuje jedno nebo více zobrazení textu. Když [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] je v režimu rozhraní více dokumentů (MDI), okno kódu je podřízený MDI. |
| Zobrazení textu | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> | Okno, které umožňuje uživateli procházet a zobrazovat text pomocí klávesnice a myši. Zobrazení textu se uživateli zobrazí jako editor. Textová zobrazení můžete použít v běžných oknech editoru, v okně Výstup a v okně Okamžité. Kromě toho můžete nakonfigurovat jedno nebo více zobrazení textu v okně kódu. |
| Správce textu | Spravuje <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> služba, ze které získáte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> ukazatel | Součást, která udržuje společné informace sdílené všemi součástmi popsanými dříve. |
| Jazyková služba | V závislosti na implementaci; Implementuje<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> | Objekt, který poskytuje editoru informace specifické pro jazyk, jako je například zvýraznění syntaxe, dokončení příkazu a porovnávání složených závorek. |

## <a name="see-also"></a>Viz také
- [Data dokumentu a zobrazení dokumentu ve vlastních editorech](../../extensibility/document-data-and-document-view-in-custom-editors.md)
