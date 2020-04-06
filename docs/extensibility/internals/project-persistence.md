---
title: Přetrvávání projektu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 10a9cde91c0181fbfefbaa353c7c3702f4b36819
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706463"
---
# <a name="project-persistence"></a>Trvalost projektu
Trvalost je klíčovým aspektem návrhu projektu. Většina projektů používá položky projektu, které představují soubory; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] podporuje také projekty, jejichž data nejsou založena na souboru. Soubory vlastněné projektem a soubor projektu musí být trvalé. IDE pokyn projektu uložit sebe nebo položku projektu.

 Šablony pro projekty jsou předány do továrny projektu. Šablony by měly podporovat inicializaci všech položek projektu podle požadavků konkrétního typu projektu. Tyto šablony mohou být později uloženy jako soubory projektu a spravovány ide prostřednictvím řešení. Další informace naleznete [v tématu Vytváření instancí projektu pomocí továren a](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) [řešení](../../extensibility/internals/solutions-overview.md)projektu .

 Položky projektu mohou být založené na souborech nebo nezaložené na souborech:

- Položky založené na souborech mohou být místní nebo vzdálené. Například ve webových projektech v systému C# připojení k souborům ve vzdáleném systému přetrvávají místně, zatímco samotné soubory ve vzdáleném systému přetrvávají.

- Položky, které nejsou založeny na souborech, mohou ukládat položky do databáze nebo úložiště.

## <a name="commit-models"></a>Modely potvrzení
 Po rozhodnutí, kde jsou položky projektu umístěny, musíte zvolit příslušný model potvrzení. Například v modelu založeném na souborech s místními soubory lze každý projekt uložit samostatně. V modelu úložiště můžete uložit několik položek v jedné transakci. Další informace naleznete v [tématu Project Type Design Decisions](../../extensibility/internals/project-type-design-decisions.md).

 Chcete-li určit přípony názvů <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> souborů, projekty implementují rozhraní, které poskytuje informace umožňující klientovi objektu implementovat dialogové okno **Uložit jako** – to znamená vyplnit rozevírací seznam **Uložit jako typ** a spravovat počáteční příponu názvu souboru.

 Rozhraní IDE `IPersistFileFormat` volá rozhraní v projektu k označení, že projekt by měl zachovat své položky projektu podle potřeby. Proto objekt vlastní všechny aspekty jeho souboru a formátu. To zahrnuje název formátu objektu.

 V případě, že položky `IPersistFileFormat` nejsou soubory, je stále, jak jsou trvalé položky ne založené na souboru. Soubory projektu, například soubory [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] VBP pro projekty nebo [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] soubory VCproj pro projekty, musí být také trvalé.

 Pro uložení akce IDE zkontroluje spuštěnou tabulku dokumentů (RDT) a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> hierarchie <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> předá příkazy a rozhraní. Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> je implementována k určení, zda byla položka změněna. Pokud položka má, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> metoda je implementována k uložení změněné položky.

 Metody na `IVsPersistHierarchyItem2` rozhraní se používají k určení, zda lze položku znovu načíst, a pokud lze položku znovu načíst. Kromě toho <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> může být metoda implementována tak, aby způsobila, že změněné položky budou zahozeny bez uložení.

## <a name="see-also"></a>Viz také
- [Kontrolní seznam: Vytvoření nových typů projektů](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Vytváření instancí projektu pomocí objektů pro vytváření projektů](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
