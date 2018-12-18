---
title: Projekt trvalost | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b85bb6155ca25abec67b582dc4d877dbd8290501
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131121"
---
# <a name="project-persistence"></a>Trvalost projektu
Trvalost je potřeba zvážit důležité pro váš projekt. Většina projektů pomocí položky projektu, které představují soubory; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] také podporuje projekty, jejichž data jsou nezaložené souboru. Oba soubory vlastněné projekt a soubor projektu musí nastavit jako trvalý. Prostředí IDE dá pokyn projekt uložit sám sebe nebo položka projektu.  
  
 Šablony pro projekty jsou předaný objekt pro vytváření projektu. Šablony by měly podporovat inicializace všechny položky projektu podle požadavků typ konkrétní projektu. Tyto šablony můžete později uloženy jako soubory projektu a spravuje IDE v řešení. Další informace najdete v tématu [vytváření instancí podle pomocí projektu objekty pro vytváření projektů](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) a [řešení](../../extensibility/internals/solutions.md).  
  
 Položky projektu může být na základě souborů nebo není určena pro soubor:  
  
-   Položky na základě souborů může být místní nebo vzdálené. Ve webové projekty v jazyce C# například připojení k souborům ve vzdáleném systému zachovat místně, zatímco na vzdáleném systému se zachovají soubory sami.  
  
-   Položky na základě bez souborů můžete uložit položky do databáze nebo úložiště.  
  
## <a name="commit-models"></a>Potvrdit modely  
 Jakmile se rozhodnete, kde jsou umístěny položky projektu, musíte zvolit odpovídající potvrzení modelu. Například v modelu na základě souborů s místní soubory, každého projektu lze uložit samostatně. V modelu úložiště můžete uložit několik položek v jedné transakci. Další informace najdete v tématu [rozhodnutí o návrhu projektu typu](../../extensibility/internals/project-type-design-decisions.md).  
  
 K určení přípony názvů souborů, implementujte projekty <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> rozhraní, která poskytuje informace o povolení klientského objektu k implementaci **uložit jako** dialogové okno – to znamená, vyplnit **uložit jako typ**  rozevírací seznam a spravovat počáteční příponu názvu.  
  
 Volání IDE `IPersistFileFormat` rozhraní na projekt, který má znamenat, že projekt by měl uchovat jeho projektu položky podle potřeby. Proto vlastní objekt všechny aspekty její soubor a formát. To zahrnuje název formátu objektu.  
  
 V případě, kdy položky nejsou soubory `IPersistFileFormat` je stále jak soubor nezaložené položky jsou nastavené jako trvalé. Soubory, jako jsou například soubory .vbp pro projektu [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projekty nebo .vcproj soubory pro [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projekty, musíte taky nastavit jako trvalý.  
  
 Pro uložení akce, rozhraní IDE prozkoumá spuštěné tabulce dokumentu (r...) a hierarchii předá příkazy službě <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> rozhraní. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> Je implementována metoda k určení, zda položka byla změněna. Pokud položka neobsahuje, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> je implementována metoda uložit upravené položky.  
  
 Metody na `IVsPersistHierarchyItem2` rozhraní se používají k určení, zda můžete znovu načíst položku, a pokud položka může být, znovu jej načíst. Kromě toho <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> může být implementována metoda způsobit změněné položky budou zahozeny bez uložení.  
  
## <a name="see-also"></a>Viz také  
 [Kontrolní seznam: Vytvoření nové typy projektu](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Vytváření instancí projektu pomocí objektů pro vytváření projektů](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)