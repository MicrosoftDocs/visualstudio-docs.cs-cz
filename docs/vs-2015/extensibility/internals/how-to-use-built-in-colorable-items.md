---
title: 'Postupy: Použití vestavěných barevně používaných položek | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a86361f28eb4c73a65093fc5c80ef15ddf791a77
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64787396"
---
# <a name="how-to-use-built-in-colorable-items"></a>Postupy: Použití předdefinovaných položek, které lze zabarvit
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Než začnete používat vestavěné položky barev, musíte nejdřív signalizovat integrované vývojové prostředí (IDE), které neposkytujete vlastní barvy, které by v tomto případě byly <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> objekty. Provedete to tak, že nastavíte položku registru pro službu jazyka.  
  
### <a name="to-use-built-in-colorable-items"></a>Použití vestavěných barevných položek  
  
1. V části HKEY_LOCAL_MACHINE \VisualStudio \\ *x. y*\Languages\Language Services \\ *název jazyka*, kde *X. y* je verze [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] a *název jazyka* je název vašeho jazyka, vytvořte hodnotu položky registru DWORD s názvem `RequestStockColors` .  
  
2. Nastavte `RequestStockColors` hodnotu položky registru na 1.  
  
     Po vytvoření položky registru <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> může metoda Colorizer použít členy <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> výčtu k vyplnění pole atributů barvy pro použití v editoru.  
  
    > [!NOTE]
    > Nenastavte tuto položku registru, Pokud poskytujete vlastní barevné položky. Další informace najdete v tématu [vlastní barevné položky](../../extensibility/internals/custom-colorable-items.md).  
  
## <a name="see-also"></a>Viz také  
 [Barevné zvýrazňování syntaxe ve vlastních editorech](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Barevné zvýrazňování syntaxe ve službě starší verze jazyka](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementace Obarvení syntaxe](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Vlastní barevné položky](../../extensibility/internals/custom-colorable-items.md)   
 [Registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service2.md)
