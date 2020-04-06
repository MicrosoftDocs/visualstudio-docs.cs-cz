---
title: Architektura typů projektů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], architecture
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e53929b1ec2ed9c73191bf16f1cedc84a53b58f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706310"
---
# <a name="project-types-architecture"></a>Architektura typů projektů
Tato část obsahuje podrobné informace o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]architektuře typů projektů v aplikaci .

## <a name="in-this-section"></a>V tomto oddílu
- [Prvky modelu projektu](../../extensibility/internals/elements-of-a-project-model.md)

 Uvádí služby, které může typ projektu využívat, a rozhraní, která musí implementovat.

- [Základní komponenty modelu projektu](../../extensibility/internals/project-model-core-components.md)

 Popisuje rozhraní typy projektu musí implementovat a volitelně můžete implementovat poskytnout další funkce.

- [Kdy vytvořit typy projektů](../../extensibility/internals/when-to-create-project-types.md)

 Pomáhá rozhodnout, kdy je nutné vytvořit typ [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projektu a kdy můžete použít jinou funkci rozšiřitelnosti, jako je například VSPackages a editory k dosažení stejného cíle.

- [Hierarchie a výběr](../../extensibility/internals/hierarchies-and-selection.md)

 Popisuje, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jak používá hierarchie a kontext výběru k zajištění konzistentního a zjednodušeného uživatelského prostředí.

## <a name="related-sections"></a>Související oddíly
- [Podtypy projektů](../../extensibility/internals/project-subtypes.md)

 Vysvětluje, jak podtypy projektu umožňují přizpůsobit chování [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projektových systémů a [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].

- [Typy projektů](../../extensibility/internals/project-types.md)

 Poskytuje přehled projektů jako základní stavební [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kameny integrovaného vývojového prostředí (IDE). Odkazy jsou k dispozici na další témata, která vysvětlují, jak projekty řídí vytváření a kompilaci kódu.
