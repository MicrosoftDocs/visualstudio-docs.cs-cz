---
title: Vnořování projektů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0e3a0fae42dc7bf1497e3d0d4a9d23f9cab50675
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "68180412"
---
# <a name="nesting-projects"></a>Vnoření projektů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vývojáři podnikových aplikací, kteří používají váš balíček vs, mohou pohodlně seskupit podobné typy projektů dohromady [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] pomocí *vnoření projektu*. Například projekt šablony organizace používá vnořené projekty k seskupení projektů do kategorií. Projekty obchodní fasády, projekty webového uživatelského rozhraní a tak dále jsou seskupeny do jedné kategorie.  
  
 V tomto scénáři neexistuje žádné omezení počtu projektů, které může vývojář vnořit do jednotlivých nadřazených projektů, i když vývojář může programově poskytnout omezení. Tento typ seskupení lze také nastavit jako rekurzivní, v takovém případě mohou být projekty stejného typu jako podřízený projekt vnořeny do podřízené položky, aby se staly dílčím projektem podřízeného prvku, který je dílčím projektem nadřazeného objektu.  
  
 Vnoření projektu není vnitřní součástí [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Je nutné napsat kód pro povolení vnoření a dílčího projektu vnoření do podřízených projektů. Nadřazený projekt je speciální VSPackage nebo typ projektu, vytvořený a registrovaný pomocí vlastního identifikátoru GUID, který obsahuje kód, který je vyžadován pro implementaci vnořování projektu.  
  
 Příklad vnořených projektů naleznete v ukázce C# příkladu. Nested. vnořený projekt.  
  
## <a name="nested-projects-example"></a>Příklad vnořených projektů  
 ![Řešení vnořených projektů](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects")  
Příklad vnořených projektů  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Implementace vnořených projektů](../../extensibility/internals/how-to-implement-nested-projects.md)   
 [Předpoklady pro uvolnění a opětovné načtení vnořených projektů](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)   
 [Podpora průvodce pro vnořené projekty](../../extensibility/internals/wizard-support-for-nested-projects.md)   
 [Registrace šablon projektů a položek](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Implementace zpracování příkazů pro vnořené projekty](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)   
 [Filtrování dialogového okna AddItem pro vnořené projekty](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)   
 [Kontrolní seznam: Vytváření nových typů projektů](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Kontextové parametry](../../extensibility/internals/context-parameters.md)   
 [Soubor průvodce (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
