---
title: Rozšiřování projektů | Microsoft Docs
description: Naučte se vytvářet vlastní typy projektů v sadě Visual Studio SDK a spravovat různé typy řešení sady Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 181acea9a5188ba28a4ef109b5bec0e7c040b5da
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994612"
---
# <a name="extend-projects"></a>Roztažení projektů
Projekty a řešení jsou způsoby, kterými Visual Studio uspořádává kód a soubory prostředků do kompilace a jednotek nasazení. Můžete najít další informace o projektech v [projektech (Visual Studio SDK)](../extensibility/extending-projects.md).

 Můžete vytvořit vlastní typy projektů pomocí sady Visual Studio SDK a spravovaného rozhraní balíčku pro projekty, které si můžete stáhnout ve [spravovaném rozhraní balíčku pro projekty](https://github.com/tunnelvisionlabs/MPFProj10). Chcete-li pochopit, jak jsou implementovány vlastní projekty, viz téma [Nová generace projektů: v digestoři, první část](../extensibility/internals/new-project-generation-under-the-hood-part-one.md) a [Nová generace projektů: v digestoři, druhá část](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 Témata v této části popisují, jak vytvořit vlastní projekty a jak spravovat různé typy řešení sady Visual Studio.

## <a name="in-this-section"></a>V této části
- [Vytvoření základního projektového systému, část 1](../extensibility/creating-a-basic-project-system-part-1.md) Popisuje, jak vytvořit vlastní systém projektu.

- [Vytvoření základního projektového systému, část 2](../extensibility/creating-a-basic-project-system-part-2.md) Popisuje, jak vytvořit vlastní systém projektu.

- [Uložení dat v souborech projektu](../extensibility/saving-data-in-project-files.md) Vysvětluje, jak přidat do projektu (<em>.</em> PROJ *) soubory.

- [Ověření podtypů projektu v době běhu](../extensibility/verifying-subtypes-of-a-project-at-run-time.md) Vysvětluje, jak ověřit podtyp projektu v době běhu.

- [Přidat a odebrat stránky vlastností](../extensibility/adding-and-removing-property-pages.md) Vysvětluje, jak přizpůsobit stránky vlastností pro vlastní projekt.

- [Přidání atributu do položky projektu](../extensibility/adding-an-attribute-to-a-project-item.md) Vysvětluje, jak přidat atribut do vlastní položky projektu.

- [Zachovat vlastnost položky projektu](../extensibility/persisting-the-property-of-a-project-item.md) Vysvětluje, jak zachovat vlastnosti vlastní položky projektu.

- [Správa univerzálních projektů pro Windows](../extensibility/managing-universal-windows-projects.md) Vysvětluje, jak spravovat univerzální projekty.
