---
title: Data dokumentů a zobrazení dokumentů ve vlastních editorech | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 04e89194ff09bc273294246cc25718c999daf70f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712136"
---
# <a name="document-data-and-document-view-in-custom-editors"></a>Zobrazení dat dokumentů a dokumentů ve vlastních editorech
Vlastní editor se skládá ze dvou částí: datového objektu dokumentu a objektu zobrazení dokumentu. Jak naznačují názvy, datový objekt dokumentu představuje textová data, která mají být zobrazena. Podobně objekt zobrazení dokumentu (nebo "zobrazení") představuje jedno nebo více oken, ve kterých se má zobrazit datový objekt dokumentu.

## <a name="document-data-object"></a>Datový objekt dokumentu
 Datový objekt dokumentu je reprezentace textu ve vyrovnávací paměti textu. Jedná se o objekt COM, který ukládá text dokumentu a další informace. Datový objekt dokumentu také zpracovává trvalost dokumentu a umožňuje více zobrazení jeho dat. Další informace najdete v tématu

 <xref:EnvDTE80.Window2.DocumentData%2A>a [dokument windows](../extensibility/internals/document-windows.md).

 Vlastní editory a návrháři <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> můžete zvolit použití objektu nebo vlastní vyrovnávací paměti. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>následuje zjednodušený model vkládání pro standardní editor, podporuje více zobrazení a poskytuje rozhraní událostí, která se používají ke správě více zobrazení.

## <a name="document-view-object"></a>Objekt zobrazení dokumentu
 Okno, které zobrazuje kód a další text, se označuje jako zobrazení nebo zobrazení dokumentu. Při vytváření editoru můžete zvolit buď jedno zobrazení, ve kterém se text zobrazí v jednom okně. Nebo můžete zvolit vícenásobné zobrazení, ve kterém je text zobrazen ve více než jednom okně. Vaše volba závisí na vaší aplikaci. Pokud například potřebujete úpravy vedle sebe, zvolíte více zobrazení. Každé zobrazení je přidruženo k položce v tabulce dokumentů (IDE) integrovaného vývojového prostředí (IDE). Okna zobrazení patří k <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> projektu nebo objektu.

 Pokud editor podporuje více zobrazení datového objektu dokumentu, musí být data dokumentu a objekty zobrazení dokumentu odděleny. V opačném případě mohou být seskupeny. Další informace naleznete v [tématu Podpora více zobrazení dokumentu](../extensibility/supporting-multiple-document-views.md).

 IDE upozorní zobrazení o událostech (například při uzavření řešení obsahujícího dokument) porovnáním identifikátoru položky (ItemID) pro každou položku v tabulce běžícího dokumentu. Další informace naleznete v tématu [Spuštění tabulky dokumentů](../extensibility/internals/running-document-table.md).

 Existují dvě možnosti pro vytvoření zobrazení pro vlastní editor. Jedním z nich je model aktivace na místě, kde je zobrazení hostováno v okně pomocí ovládacího prvku ActiveX nebo datového objektu dokumentu. Druhým je zjednodušený model vkládání, kde je [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zobrazení <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> hostováno a implementováno pro zpracování příkazů okna. Informace o modelu aktivace na místě naleznete [v tématu Aktivace na místě](/visualstudio/misc/in-place-activation?view=vs-2015). Informace o zjednodušeném modelu vkládání naleznete v [tématu Zjednodušené vkládání](../extensibility/simplified-embedding.md).

## <a name="see-also"></a>Viz také

- [Podpora více zobrazení dokumentu](../extensibility/supporting-multiple-document-views.md)
- [Zjednodušené vkládání](../extensibility/simplified-embedding.md)
- [Postup: Připojení zobrazení k datům dokumentu](../extensibility/how-to-attach-views-to-document-data.md)
- [Správa držáku zámku dokumentu](../extensibility/document-lock-holder-management.md)
- [Zobrazení s jednou a více kartami](../extensibility/single-and-multi-tab-views.md)
- [Uložení standardního dokumentu](../extensibility/internals/saving-a-standard-document.md)
- [Trvalost a spuštěná tabulka dokumentů](../extensibility/internals/persistence-and-the-running-document-table.md)
- [Určení editoru, který otevře soubor v projektu](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)
