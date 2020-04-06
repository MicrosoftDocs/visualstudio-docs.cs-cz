---
title: Rozšíření projektů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- projects [Visual Studio]
ms.assetid: 096d273d-4fe9-4f24-9b00-470bfbdf4bdf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14108a304cc5f85c9a870bc66804df7daa98f3ca
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711753"
---
# <a name="extend-projects"></a>Rozšířit projekty
Projekty a řešení jsou způsoby, jakými Visual Studio organizuje soubory kódu a prostředků do jednotek kompilace a nasazení. Další informace o projektech naleznete v [aplikaci Projects (Visual Studio SDK).](../extensibility/extending-projects.md)

 Vlastní typy projektů můžete vytvořit pomocí sady Visual Studio SDK a rozhraní Managed Package Framework for Projects, které si můžete stáhnout v [rámci spravovaného balíčku pro projekty](https://github.com/tunnelvisionlabs/MPFProj10). Chcete-li pochopit, jak jsou implementovány vlastní projekty, viz [Nové generování projektu: Pod kapotou, první část](../extensibility/internals/new-project-generation-under-the-hood-part-one.md) a Nová generace [projektu: Pod kapotou, část druhá](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 Témata v této části popisují, jak vytvořit vlastní projekty a jak spravovat různé typy řešení sady Visual Studio.

## <a name="in-this-section"></a>V tomto oddílu
- [Vytvoření základního projektového systému, část 1](../extensibility/creating-a-basic-project-system-part-1.md) Popisuje, jak vytvořit vlastní systém projektu.

- [Vytvoření základního projektového systému, část 2](../extensibility/creating-a-basic-project-system-part-2.md) Popisuje, jak vytvořit vlastní systém projektu.

- [Uložení dat do souborů projektu](../extensibility/saving-data-in-project-files.md) Vysvětluje, jak přidat do projektu (<em>.</em> proj*).

- [Ověření podtypů projektu za běhu](../extensibility/verifying-subtypes-of-a-project-at-run-time.md) Vysvětluje, jak ověřit podtyp projektu za běhu.

- [Přidání a odebrání stránek vlastností](../extensibility/adding-and-removing-property-pages.md) Vysvětluje, jak přizpůsobit stránky vlastností pro vlastní projekt.

- [Přidání atributu k položce projektu](../extensibility/adding-an-attribute-to-a-project-item.md) Vysvětluje, jak přidat atribut do vlastní položky projektu.

- [Zachovat vlastnost položky projektu](../extensibility/persisting-the-property-of-a-project-item.md) Vysvětluje, jak zachovat vlastnosti vlastní položky projektu.

- [Správa univerzálních projektů systému Windows](../extensibility/managing-universal-windows-projects.md) Vysvětluje, jak řídit univerzální projekty.
