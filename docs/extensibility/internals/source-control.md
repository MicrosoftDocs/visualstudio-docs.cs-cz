---
title: Správa zdrojového kódu | Microsoft Docs
description: Tyto články popisují možnosti implementace správy zdrojového kódu jako integrované funkce sady Visual Studio, a to buď pomocí modulu plug-in, nebo VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK]
ms.assetid: 13d5728c-4e28-42e4-944a-a565b1765ef8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 99c19fd202cf0e9fe56ba6485aaa1a7005047774
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064063"
---
# <a name="source-control"></a>Správa zdrojového kódu
Tato část popisuje možnosti pro implementaci správy zdrojového kódu jako integrované funkce nástroje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , buď prostřednictvím modulu plug-in správy zdrojových kódů, nebo balíčku VSPackage správy zdrojového kódu.

## <a name="in-this-section"></a>V tomto oddílu
- [Essentials](../../extensibility/internals/source-control-integration-essentials.md)

 Obsahuje důležité informace, které je nutné pro zahájení práce se správou zdrojových kódů.

- [Přehled](../../extensibility/internals/source-control-integration-overview.md)

 Přehled dvou dostupných možností pro implementaci správy zdrojového kódu.

- [Vytvoření modulu plug-in správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-plug-in.md)

 Popisuje, jak vytvořit modul plug-in správy zdrojového kódu, který poskytuje funkce správy zdrojového kódu prostřednictvím [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] uživatelského rozhraní správy zdrojového kódu (UI).

- [Vytvoření balíčku VSPackage správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Popisuje, jak vytvořit prvek VSPackage správy zdrojového kódu, který neposkytuje pouze funkce správy zdrojového kódu, ale lze jej použít k přizpůsobení [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] uživatelského rozhraní správy zdrojového kódu.

## <a name="related-sections"></a>Související oddíly
- [Moduly plug-in správy zdrojového kódu](../../extensibility/source-control-plug-ins.md)

 Odkaz na rozhraní API pro modul plug-in správy zdrojového kódu

- [Rozšíření projektů](../../extensibility/extending-projects.md)

 Popisuje, jak používat [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projekty a řešení k uspořádání souborů kódu a souborů prostředků a jak implementovat správu zdrojového kódu.
