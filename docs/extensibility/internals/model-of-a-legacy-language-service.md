---
title: Model služby starší verze jazyka | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 381c5b37cdc5d8a166003bdf7dd931dd95e6dcb3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49943086"
---
# <a name="model-of-a-legacy-language-service"></a>Model služby starší verze jazyka
Služba jazyka definuje prvky a funkce pro konkrétní jazyk a slouží k poskytování editoru pomocí informací specifických pro daný jazyk. Editor například potřebuje vědět elementy a klíčová slova jazyka za účelem podpory barevné zvýrazňování syntaxe.  
  
 Služba jazyka úzce spolupracuje s textovou vyrovnávací paměť spravuje se v editoru a zobrazení, která obsahuje editor. Microsoft IntelliSense **rychlé informace** možnost je příkladem funkcí poskytovaný službou jazyka.  
  
## <a name="a-minimal-language-service"></a>Minimální jazykový služby  
 Nejzákladnější language service obsahuje následující dva objekty:  
  
- *Jazyková služba* implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> rozhraní. Jazyk služba má informace o jazyce, včetně názvu, přípony názvů souborů, Správce oken kódu a colorizer.  
  
- *Colorizer* implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> rozhraní.  
  
  Následující koncepční nákres znázorňuje model služby základního jazyka.  
  
  ![Obrázek modelu služby jazyka](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
  Základní jazyk modelu služby  
  
  Hostitelé okna dokumentu *dokumentu zobrazení* editoru, v tomto případě [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] základní editor. Zobrazení dokumentu a textové vyrovnávací paměti jsou vlastněny editoru. Tyto objekty pracovat [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prostřednictvím okna specializované dokumentu volána *okno kódu*. Okno kódu je součástí <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objekt, který je vytvořen a řídí integrovaného vývojového prostředí.  
  
  Při načítání souboru s příponou dané editoru vyhledá služba jazyka, které jsou přidružené k rozšíření a předá do něj okna kódu voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> metody. Tato služba vrátí hodnotu jazyka *Správce oken kód*, která implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> rozhraní.  
  
  Následující tabulka obsahuje přehled objekty v modelu.  
  
| Součást | Objekt | Funkce |
|------------------| - | - |
| Vyrovnávací paměť textu | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> | Kódování Unicode pro čtení a zápis textového datového proudu. Je možné, text, který používají jiné kódování. |
| Okno kódu | <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> | Okno dokumentu, který obsahuje jedno nebo více zobrazení textu. Když [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] je v režimu rozhraní více dokumentů (MDI), okno kódu je podřízeným MDI. |
| Zobrazení textu | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> | Okno, které umožní uživateli procházení a zobrazení textu pomocí klávesnice a myši. Zobrazení textu se uživateli zobrazí jako editor. Můžete použít zobrazení textu v běžném editoru windows, v okně Výstup a podokna. Kromě toho můžete nakonfigurovat jeden nebo více zobrazení textu v okně kódu. |
| Textový správce | Spravuje <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> služby, ze kterého můžete získat <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> ukazatele | Komponenta, která udržuje běžných informací o sdílené všemi komponentami, které je popsáno výše. |
| Služba jazyka | Implementace závislé; implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> | Objekt, který poskytuje informace specifické pro jazyk zvýraznění syntaxe, dokončování příkazů a párování složených závorek v editoru. |
  
## <a name="see-also"></a>Viz také  
 [Data dokumentu a zobrazení dokumentu ve vlastních editorech](../../extensibility/document-data-and-document-view-in-custom-editors.md)