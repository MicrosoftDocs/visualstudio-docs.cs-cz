---
title: Trvalost projektu | Microsoft Docs
description: Přečtěte si o persistenci v návrhu projektu, včetně použití IPersistFileFormat k uchovávání souborů i souborů projektů, které nejsou založené na souboru.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2ffaeb6d43597e93586db79c305b654b42bf6dbb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062795"
---
# <a name="project-persistence"></a>Trvalost projektu
Trvalost je klíčovým aspektem návrhu projektu. Většina projektů používá položky projektu, které reprezentují soubory; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] podporuje také projekty, jejichž data nejsou založená na souborech. Oba soubory vlastněné projektem a soubor projektu musí být trvalé. Rozhraní IDE instruuje projekt, aby uložil sám sebe nebo položku projektu.

 Šablony pro projekty jsou předány do objektu pro vytváření projektu. Šablony by měly podporovat inicializaci všech položek projektu podle požadavků konkrétního typu projektu. Tyto šablony mohou být později uloženy jako soubory projektu a spravovány pomocí integrovaného vývojového prostředí (IDE) prostřednictvím řešení. Další informace naleznete v tématu [vytváření instancí projektu pomocí továrnování](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) a [řešení](../../extensibility/internals/solutions-overview.md)projektu.

 Položky projektu můžou být založené na souborech nebo nezaložené na souborech:

- Položky založené na souborech můžou být místní nebo vzdálené. Ve webových projektech v jazyce C#, například připojení k souborům ve vzdáleném systému, zůstávají lokálně trvalé, zatímco samotné soubory zůstávají na vzdáleném systému.

- Položky, které nejsou založené na souboru, můžou ukládat položky do databáze nebo úložiště.

## <a name="commit-models"></a>Modely potvrzení
 Po rozhodnutí, kde jsou umístěny položky projektu, je nutné zvolit příslušný model potvrzení. Například v modelu založeném na souborech s místními soubory lze každý projekt uložit samostatně. V modelu úložiště můžete uložit několik položek v jedné transakci. Další informace naleznete v tématu [rozhodnutí o návrhu typu projektu](../../extensibility/internals/project-type-design-decisions.md).

 Aby bylo možné určit přípony názvů souborů, projekty implementují <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> rozhraní, které poskytuje informace umožňující klientovi objektu implementovat dialogové okno **Uložit jako** – to znamená vyplnit v rozevíracím seznamu **Uložit jako typ** a spravovat počáteční příponu názvu souboru.

 Rozhraní IDE volá `IPersistFileFormat` rozhraní na projektu, aby označovalo, že projekt by měl uchovávat své položky projektu podle potřeby. Proto objekt vlastní všechny aspekty jeho souboru a formátu. To zahrnuje název formátu objektu.

 V případě, že položky nejsou soubory, `IPersistFileFormat` je stále i způsob, jakým jsou trvalé položky založené na souborech. Soubory projektu, například soubory. vbp pro [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projekty nebo soubory. vcproj pro [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projekty, musí být také trvalé.

 V případě akcí uložit rozhraní IDE ověří tabulku běžícího dokumentu (RDT) a hierarchie předá příkazy do <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> rozhraní a rozhraní. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A>Metoda je implementována k určení, zda byla položka upravena. Pokud má položka <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> hodnotu, je implementována metoda pro uložení upravené položky.

 Metody na `IVsPersistHierarchyItem2` rozhraní se používají k určení, zda lze položku znovu načíst a zda může být položka znovu načtena. Kromě toho je <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> možné implementovat metodu, která způsobí, že se změněné položky zruší bez uložení.

## <a name="see-also"></a>Viz také
- [Kontrolní seznam: Vytvoření nových typů projektů](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Vytváření instancí projektu pomocí objektů pro vytváření projektů](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
