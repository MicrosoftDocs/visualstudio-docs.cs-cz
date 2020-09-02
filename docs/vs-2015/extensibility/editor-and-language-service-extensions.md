---
title: Rozšíření pro Editor a jazykové služby | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7fa3e4be6ee44011eb1286e3ebf22ee69f8e3397
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683119"
---
# <a name="editor-and-language-service-extensions"></a>Editor a rozšíření služeb jazyka
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Většinu funkcí editoru kódu sady Visual Studio můžete zvětšit. Editor je založen na Windows Presentation Foundation (WPF) a je napsán ve spravovaném kódu. I když se tento návrh liší od návrhů v dřívějších verzích sady Visual Studio, poskytuje většinu stejných funkcí. Chcete-li Editor roztáhnout, použijte Managed Extensibility Framework (MEF).  
  
 Sada Visual Studio SDK poskytuje adaptéry označované jako *překrytí* , aby podporovaly sady VSPackage napsané pro starší verze. Nicméně pokud máte existující VSPackage, doporučujeme, abyste ho aktualizovali na novou technologii, abyste získali lepší výkon a spolehlivost.  
  
## <a name="related-topics"></a>Související témata  
  
|Nadpis|Popis|  
|-----------|-----------------|  
|[Vytváření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Seznámení s použitím šablon položek editoru|  
|[Rozšíření pro editor a služeb jazyka](../extensibility/extending-the-editor-and-language-services.md)|Odkazuje na dokumenty, které zavádějí návrh a funkce základního editoru a ukazují, jak ho zvětšit.|  
|[Zastaralá rozhraní v editoru](../extensibility/legacy-interfaces-in-the-editor.md)|Odkazuje na dokumenty, které vysvětlují přístup k základnímu editoru z existujícího kódu.|  
|[Vytváření vlastních editorů a návrhářů](../extensibility/creating-custom-editors-and-designers.md)|Odkazuje na dokumenty, které vysvětlují, jak vytvořit vlastní editory.|  
|[Rozšíření služeb starší verze jazyka](../extensibility/internals/legacy-language-service-extensibility.md)|Odkazuje na dokumenty, které popisují integraci programovacích jazyků do sady Visual Studio.|  
|[Managed Extensibility Framework (MEF)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|Zavádí Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](https://msdn.microsoft.com/library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|Zavádí Windows Presentation Foundation (WPF).|
