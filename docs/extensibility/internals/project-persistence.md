---
title: Trvalost projektu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a95c919de9b87ed1782cbdcb029efbf191958f5a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725454"
---
# <a name="project-persistence"></a>Trvalost projektu
Trvalost je klíčovým aspektem návrhu projektu. Většina projektů používá položky projektu, které reprezentují soubory;  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] také podporuje projekty, jejichž data nejsou založená na souborech. Oba soubory vlastněné projektem a soubor projektu musí být trvalé. Rozhraní IDE instruuje projekt, aby uložil sám sebe nebo položku projektu.

 Šablony pro projekty jsou předány do objektu pro vytváření projektu. Šablony by měly podporovat inicializaci všech položek projektu podle požadavků konkrétního typu projektu. Tyto šablony mohou být později uloženy jako soubory projektu a spravovány pomocí integrovaného vývojového prostředí (IDE) prostřednictvím řešení. Další informace naleznete v tématu [vytváření instancí projektu pomocí továrnování](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) a [řešení](../../extensibility/internals/solutions-overview.md)projektu.

 Položky projektu můžou být založené na souborech nebo nezaložené na souborech:

- Položky založené na souborech můžou být místní nebo vzdálené. Ve webových projektech v C#, například připojení k souborům ve vzdáleném systému trvale přetrvává, zatímco samotné soubory zůstávají na vzdáleném systému.

- Položky, které nejsou založené na souboru, můžou ukládat položky do databáze nebo úložiště.

## <a name="commit-models"></a>Modely potvrzení
 Po rozhodnutí, kde jsou umístěny položky projektu, je nutné zvolit příslušný model potvrzení. Například v modelu založeném na souborech s místními soubory lze každý projekt uložit samostatně. V modelu úložiště můžete uložit několik položek v jedné transakci. Další informace naleznete v tématu [rozhodnutí o návrhu typu projektu](../../extensibility/internals/project-type-design-decisions.md).

 Aby bylo možné určit přípony názvů souborů, projekty implementují rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>, které poskytuje informace umožňující klientovi objektu implementovat dialogové okno **Uložit jako** – to znamená vyplnit v rozevíracím seznamu **Uložit jako typ** a spravovat počáteční přípona názvu souboru

 Rozhraní IDE volá `IPersistFileFormat` rozhraní projektu, aby označovalo, že projekt by měl uchovávat své položky projektu podle potřeby. Proto objekt vlastní všechny aspekty jeho souboru a formátu. To zahrnuje název formátu objektu.

 V případě, že položky nejsou soubory, `IPersistFileFormat` stále ještě nesouborové položky, které jsou zachovány. Soubory projektu, například soubory. vbp pro [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projekty nebo soubory. vcproj pro [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projekty, musí být také trvalé.

 V případě akcí uložit ověří rozhraní IDE tabulku běžícího dokumentu (RDT) a hierarchie předá příkazy do <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> rozhraní. K určení, zda byla položka změněna, je implementována metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A>. Pokud má položka hodnotu, je implementována metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> pro uložení upravené položky.

 Metody v rozhraní `IVsPersistHierarchyItem2` slouží k určení, zda lze položku znovu načíst a zda může být položka znovu načtena. Kromě toho je možné implementovat metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A>, která způsobí, že změněné položky budou zahozeny bez uložení.

## <a name="see-also"></a>Viz také:
- [Kontrolní seznam: Vytvoření nových typů projektů](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Vytváření instancí projektu pomocí objektů pro vytváření projektů](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)