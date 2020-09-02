---
title: Rozšíření sady nástrojů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- tools [Visual Studio], Toolbox
- Toolbox [Visual Studio SDK]
ms.assetid: bb84a79e-cd4c-4a58-8871-2513e7119b6e
caps.latest.revision: 38
manager: jillfra
ms.openlocfilehash: ddf67fba3ae603dbd31d4628c61a6f14cc2441c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686936"
---
# <a name="extending-the-toolbox"></a>Rozšíření panelu nástrojů
[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **Sada nástrojů** poskytuje kolekci objektů, které poskytují funkce editorům a návrhářům prostřednictvím mechanismu přetažení integrovaného vývojového prostředí (IDE).  
  
 Existují dva základní způsoby, jak sada VSPackage funguje se sadou [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **nástrojů**:  
  
- VSPackage může přidat nové datové položky a ovládací prvky do **sady nástrojů**.  
  
- VSPackage může být cílová nebo spotřebitel existující funkce **sady nástrojů** , která podporuje operace přetažení a konfiguraci vzhledu **sady nástrojů**.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: vytvoření ovládacího prvku panelu nástrojů, který používá model Windows Forms](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md)  
 Popisuje, jak vytvořit ovládací prvek sady nástrojů pomocí šablony ovládacího prvku panelu nástrojů model Windows Forms.  
  
 [Vytvoření ovládacího prvku panelu nástrojů WPF](../extensibility/creating-a-wpf-toolbox-control.md)  
 Popisuje vytvoření ovládacího prvku panelu nástrojů pomocí šablony ovládacího prvku sady nástrojů WPF.  
  
 [Správa sady nástrojů](../misc/managing-the-toolbox.md)  
 Popisuje, jak může VSPackage spravovat obsah a vzhled sady **nástrojů**.  
  
## <a name="related-sections"></a>Související oddíly  
 [Postupy: Správa okna nástrojů](https://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2)  
 Popisuje, jak pracovat se sadou **nástrojů** v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrovaném vývojovém prostředí (IDE).  
  
 [Postupy: řízení panelu nástrojů](https://msdn.microsoft.com/library/c9d8a18a-d2bc-43d4-a803-601bfc6a6599)  
 Popisuje, jak spravovat **sadu nástrojů** pomocí programovacího modelu automatizace.  
  
 [Rozšíření dalších částí sady Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Vysvětluje, jak používat [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] služby k vytvoření prvků uživatelského rozhraní, které se shodují se zbytkem z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .