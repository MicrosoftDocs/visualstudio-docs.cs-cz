---
title: Zobrazení dat dokumentů a dokumentů ve vlastních editorech | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2f73ffde43f2ef3608ae492a9643f7920243d818
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204681"
---
# <a name="document-data-and-document-view-in-custom-editors"></a>Data dokumentu a zobrazení dokumentu ve vlastních editorech
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vlastní editor se skládá ze dvou částí: datového objektu dokumentu a objektu zobrazení dokumentu. Jak naznačuje názvy, objekt data dokumentu představuje textová data, která se mají zobrazit, a objekt zobrazení dokumentu (nebo "zobrazení") představuje jedno nebo více oken, ve kterých se má zobrazit datový objekt dokumentu.  
  
## <a name="document-data-object"></a>Datový objekt dokumentu  
 Datový objekt dokumentu je reprezentace textu ve vyrovnávací paměti textu. Jedná se o objekt modelu COM, který ukládá text dokumentu a další informace, zpracovává trvalost dokumentů a umožňuje více zobrazení dat. Další informace najdete v tématu  
  
 <xref:EnvDTE80.Window2.DocumentData%2A> a [okna dokumentů](../extensibility/internals/document-windows.md).  
  
 Vlastní editory a návrháři se můžou rozhodnout použít tento <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objekt nebo vlastní vyrovnávací paměť. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> postupuje podle zjednodušeného modelu vložení pro standardní editor, podporuje více zobrazení a poskytuje rozhraní událostí, která se používají ke správě více zobrazení.  
  
## <a name="document-view-object"></a>Objekt zobrazení dokumentu  
 Okno, které zobrazuje kód a jiný text, je označováno jako zobrazení dokumentu nebo zobrazení. Když vytváříte editor, můžete zvolit jedno zobrazení, ve kterém se zobrazí text v jednom okně, nebo na více zobrazení, kde se text zobrazí ve více než jednom okně. Vaše volba závisí na vaší aplikaci. Pokud například potřebujete souběžné úpravy, vyberte možnost více zobrazení. Každé zobrazení je přidruženo k položce v integrovaném vývojovém prostředí (IDE) s tabulkou dokumentů (RDT). Zobrazení oken patří do projektu nebo <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objektu.  
  
 Pokud editor podporuje více zobrazení datového objektu dokumentu, musí být vaše data dokumentu a objekty zobrazení dokumentu oddělené. V opačném případě mohou být seskupeny dohromady. Další informace najdete v tématu [Podpora více zobrazení dokumentů](../extensibility/supporting-multiple-document-views.md).  
  
 Rozhraní IDE oznamuje zobrazení o událostech (například při zavření řešení obsahujícího dokument) porovnáním identifikátoru položky (ItemID) pro každou položku v běžící tabulce dokumentů. Další informace najdete v tématu [Spuštění tabulky dokumentů](../extensibility/internals/running-document-table.md).  
  
 Existují dvě možnosti pro vytvoření zobrazení vlastního editoru. Jedním z nich je místní aktivační model, ve kterém je zobrazení hostováno v okně pomocí ovládacího prvku ActiveX nebo datového objektu dokumentu. Druhým je zjednodušený model vkládání, ve kterém je zobrazení hostováno [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] a <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> je implementováno pro zpracování příkazů okna. Informace o integrovaném modelu aktivace najdete v tématu [Aktivace na místě](../misc/in-place-activation.md). Informace o zjednodušeném modelu vkládání najdete v tématu [zjednodušené vkládání](../extensibility/simplified-embedding.md).  
  
## <a name="see-also"></a>Viz také  
 [Podpora více zobrazení dokumentů](../extensibility/supporting-multiple-document-views.md)   
 [Zjednodušené vkládání](../extensibility/simplified-embedding.md)   
 [Postupy: připojení zobrazení k datům dokumentu](../extensibility/how-to-attach-views-to-document-data.md)   
 [Správa držitele zámku dokumentu](../extensibility/document-lock-holder-management.md)   
 [Zobrazení s jedním a více kartami](../extensibility/single-and-multi-tab-views.md)   
 [Uložení standardního dokumentu](../extensibility/internals/saving-a-standard-document.md)   
 [Trvalá a spuštěná tabulka dokumentů](../extensibility/internals/persistence-and-the-running-document-table.md)   
 [Určení editoru, který otevře soubor v projektu](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)   
 [Objekty pro vytváření editoru](../extensibility/editor-factories.md)
