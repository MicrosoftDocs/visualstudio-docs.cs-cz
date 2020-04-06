---
title: Projekty vhnízdění | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 814780fa8e7e57a022a75b2e09115cfa55a1b8be
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707035"
---
# <a name="nesting-projects"></a>Vnoření projektů
Vývojáři podnikových aplikací, kteří používají váš balíček VS, mohou pohodlně seskupit podobné typy projektů společně [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pomocí *vnoření projektu*. Například projekt Šablony organizace používá vnořené projekty k seskupení projektů do kategorií. Projekty obchodní fasády, projekty webového uživatelského uživatelského nastavení a tak dále jsou seskupeny do jedné kategorie.

 V tomto scénáři neexistuje žádné omezení počtu projektů, které může vývojář vnořit do každého nadřazeného projektu, i když vývojář může programově poskytnout omezení. Tento typ seskupení lze také rekurzivní, v takovém případě projekty stejného typu jako podřízený projekt mohou být vnořeny pod podřízený, aby se stal dílčí projekt podřízeného, což je dílčí projekt nadřazeného projektu.

 Vnoření projektu není nedílnou součástí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]aplikace . Musíte napsat kód povolit vnoření a vnoření dílčího projektu v podřízených projektech. Nadřazený projekt je speciální VSPackage, nebo typ projektu, vytvořené a registrované s vlastním identifikátorem GUID, který obsahuje kód, který je nutný k implementaci vnoření projektu.

 Příklad vnoření projektů najdete v části [Postup: Implementace vnořených projektů](../../extensibility/internals/how-to-implement-nested-projects.md).

## <a name="nested-projects-example"></a>Příklad vnořených projektů
 ![Řešení vnořených projektů](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects") Příklad vnořených projektů

## <a name="see-also"></a>Viz také
- [Důležité informace pro uvolnění a opětovné načtení vnořených projektů](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [Podpora průvodce pro vnořené projekty](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Registrace šablon projektů a položek](../../extensibility/internals/registering-project-and-item-templates.md)
- [Implementace zpracování příkazů pro vnořené projekty](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [Filtrování dialogového okna Přidat položku pro vnořené projekty](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)
- [Kontrolní seznam: Vytvoření nových typů projektů](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Parametry kontextu](../../extensibility/internals/context-parameters.md)
- [Soubor průvodce (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
