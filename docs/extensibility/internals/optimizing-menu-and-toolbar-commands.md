---
title: Optimalizace nabídky a příkazy nástrojů | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands [Visual Studio], menus
- commands [Visual Studio], toolbars
- menus [Visual Studio SDK], commands
- menu commands, implementing
- toolbars [Visual Studio], commands
ms.assetid: 8385f1a6-1e98-4dca-83d2-fcbed7177242
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 92072668f96a69a0dc5ff78839b54fa7ecc656bd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130726"
---
# <a name="optimizing-menu-and-toolbar-commands"></a>Optimalizace nabídek a příkazů panelu nástrojů
Přidání VSPackages a jejich odpovídající příkazů [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] může způsobit frekventované uživatelského rozhraní. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] poskytuje způsoby, jak zachování přehlednosti příkaz uživatelského rozhraní.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Zpřístupnění příkazů](../../extensibility/internals/making-commands-available.md)  
 Obsahuje obecné pokyny pro minimalizaci nakupením [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] uživatelského rozhraní při přidání VSPackages.  
  
 [Pokyny pro umístění](../../extensibility/internals/command-placement-guidelines.md)  
 Poskytuje konkrétní pokyny pro implementaci VSPackage na základě velikosti sadu příkazů.  
  
## <a name="related-sections"></a>Související oddíly  
 [Příkazy, nabídky a panely nástrojů](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Vysvětluje, jak vytvářet uživatelské rozhraní, které obsahuje nabídky, panely nástrojů a příkaz pole se seznamem.