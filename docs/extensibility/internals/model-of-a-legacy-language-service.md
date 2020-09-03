---
title: Model služby starší verze jazyka | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707038"
---
# <a name="model-of-a-legacy-language-service"></a>Model služby starší verze jazyka
Jazyková služba definuje prvky a funkce pro určitý jazyk a slouží k tomu, aby Editor poskytoval informace, které jsou specifické pro daný jazyk. Editor například potřebuje znát prvky a klíčová slova jazyka, aby bylo možné podporovat barevné zvýrazňování syntaxe.

 Služba jazyka úzce spolupracuje s textovou vyrovnávací pamětí spravovanou editorem a zobrazením, které obsahuje editor. **Rychlá informace** Microsoft IntelliSense je příkladem funkce poskytované jazykovou službou.

## <a name="a-minimal-language-service"></a>Minimální jazyková služba
 Nejzákladnější jazyková služba obsahuje následující dva objekty:

- *Jazyková služba* implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> rozhraní. Jazyková služba obsahuje informace o jazyce, včetně jeho názvu, přípon názvů souborů, správce oken kódu a colorizer.

- Rozhraní *Colorizer* implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> rozhraní.

  Následující koncepční vykreslení znázorňuje model základní jazykové služby.

  ![Obrázek modelu jazykové služby](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel") Model základní jazykové služby

  Okno dokumentu hostuje *zobrazení dokumentu* editoru, v tomto případě [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] základní editor. Zobrazení dokumentu a vyrovnávací paměť textu jsou vlastněny editorem. Tyto objekty pracují s [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] použitím specializovaného okna dokumentu nazývaného *okno kódu*. Okno Code je obsaženo v <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objektu, který je vytvořen a ovládán rozhraním IDE.

  Když je načten soubor s daným rozšířením, Editor vyhledá jazykovou službu přidruženou k danému rozšíření a předá ho do okna Code voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> metody. Služba jazyka vrátí *správce okna kódu*, který implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> rozhraní.

  Následující tabulka poskytuje přehled objektů v modelu.

| Součást | Objekt | Funkce |
|------------------| - | - |
| Vyrovnávací paměť textu | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> | Textový Stream pro čtení a zápis v kódování Unicode. Je možné, že text bude používat jiné kódování. |
| Okno kódu | <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> | Okno dokumentu, které obsahuje jedno nebo více textových zobrazení. Když [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] je v režimu MDI (Multiple Document Interface), je okno Code podřízenou položkou MDI. |
| Textové zobrazení | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> | Okno, které uživateli umožňuje procházet a zobrazovat text pomocí klávesnice a myši. Zobrazení textu se zobrazí uživateli jako editor. Můžete použít zobrazení textu v běžných oknech editoru, v okně výstup a v příkazovém podokně. Kromě toho můžete v okně kódu nakonfigurovat jedno nebo více textových zobrazení. |
| Správce textu | Spravováno <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> službou, ze které získáváte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> ukazatel | Komponenta, která uchovává společné informace sdílené všemi dříve popsanými komponentami. |
| Služba jazyka | Závislá implementace; implementace <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> | Objekt, který poskytuje editor s informacemi, které jsou specifické pro jazyk, jako je například zvýrazňování syntaxe, dokončování příkazů a shoda složených závorek. |

## <a name="see-also"></a>Viz také
- [Data dokumentu a zobrazení dokumentu ve vlastních editorech](../../extensibility/document-data-and-document-view-in-custom-editors.md)
