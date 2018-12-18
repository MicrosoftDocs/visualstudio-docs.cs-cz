---
title: Trvalost projektu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ff836f56601adeba7b3df675207701f6e2d6e7fa
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51729567"
---
# <a name="project-persistence"></a>Trvalost projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Trvalost se v úvahu důležité pro váš projekt. Většina projektů pomocí položky projektu, které představují soubory. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] také podporuje projekty, jejichž data jsou v jiných souborech založené. Musíte nastavit jako trvalý, soubory vlastněné projektu a souboru projektu. Rozhraní IDE nastaví projekt tak, aby uložit samotné nebo položky projektu.  
  
 Šablony pro projekty se předají objekt pro vytváření projektu. Šablony by měly podporovat inicializace všechny položky projektu podle požadavků konkrétního typu projektu. Tyto šablony lze později uloženy jako soubory projektu a spravovat pomocí rozhraní IDE v řešení. Další informace najdete v tématu [vytváření instancí podle pomocí projektu objekty pro vytváření projektů](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) a [řešení](../../extensibility/internals/solutions.md).  
  
 Položky projektu může být založené na souboru nebo jiné file-based:  
  
-   Souborové položky může být místní nebo vzdálené. Ve webové projekty v jazyce C# například připojení k souborům ve vzdáleném systému zachovat místně, zatímco podotknout zachovat ve vzdáleném systému.  
  
-   Non-file-based položky uložit položky databáze nebo úložiště.  
  
## <a name="commit-models"></a>Potvrdit modelů  
 Po rozhodnutí, kde jsou umístěné položky projektu, je nutné zvolit model příslušné potvrzení. Například v modelu na základě souboru s místními soubory, každý může být projekt uložen samostatně. V modelu úložiště můžete uložit několik položek v rámci jedné transakce. Další informace najdete v tématu [rozhodnutí o návrhu typu projektu](../../extensibility/internals/project-type-design-decisions.md).  
  
 Chcete-li určit přípony názvů souborů, projektů implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> rozhraní, který poskytuje informace o povolení klientského objektu k implementaci **uložit jako** dialogové okno – to znamená, vyplnit **uložit jako typ**  rozevíracího seznamu a spravovat počáteční příponu názvu.  
  
 Volání rozhraní IDE `IPersistFileFormat` rozhraní na projektu označuje, že projekt byste neměli zachovat jeho projektu položky podle potřeby. Proto objekt vlastní všechny prvky jeho souboru a formát. To zahrnuje název formát objektu.  
  
 V případě, kdy položky nejsou soubory `IPersistFileFormat` je stále jak bez file-based položky jsou trvalé. Soubory, jako je například .vbp soubory projektu [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] projekty nebo .vcproj soubory pro [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] projektů, musíte také nastavit jako trvalý.  
  
 Pro uložení akce, rozhraní IDE zkontroluje spuštěnou tabulku dokumentů (r...) a hierarchii předá příkazy službě <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> rozhraní. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> Metoda je implementováno s cílem zjistit, zda položka byla změněna. Pokud položka neobsahuje, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> metoda je implementována k uložení upravené položky.  
  
 Metody `IVsPersistHierarchyItem2` rozhraní se používají k určení, zda je možné znovu zavést položku, a pokud položku lze jej znovu načíst. Kromě toho <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> metodu je možné implementovat způsobit změněných položek ke zahodí bez uložení.  
  
## <a name="see-also"></a>Viz také  
 [Kontrolní seznam: Vytvoření nových typů projektů](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Vytváření instancí projektu pomocí objektů pro vytváření projektů](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

