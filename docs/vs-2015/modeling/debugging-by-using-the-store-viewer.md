---
title: Ladění pomocí prohlížeče Store | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, store viewer
- Domain-Specific Language, store
ms.assetid: 0178db2e-ae99-4ed3-9b87-8620fa9fa8e4
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 78a7cad2db2efa8057f2b95d117f93c59cc328cb
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49189072"
---
# <a name="debugging-by-using-the-store-viewer"></a>Ladění pomocí Prohlížeče ukládání
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí prohlížeče Store můžete zkontrolovat stav *ukládání* používané [!INCLUDE[dsl](../includes/dsl-md.md)]. Prohlížeč Store zobrazí všechny elementy modelu domény, které jsou v konkrétní úložiště, společně s vlastností elementů a propojení mezi elementy.  
  
## <a name="opening-store-viewer"></a>Store otevírací prohlížeče  
 Pokud pracujete s [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] experimentální sestavení, zastavte kódu na zarážce, kde instance úložiště obsahuje informace o modelu. Potom otevřete prohlížeč Store tak, že zadáte následující příkaz v **okamžité** okno:  
  
```  
Microsoft.VisualStudio.Modeling.Diagnostics.StoreViewer.Show(mystore);  
```  
  
> [!NOTE]
>  Je třeba nahradit `mystore` s názvem instance vašeho úložiště. Navíc pokud chcete přidat obor názvů do vašeho kódu, můžete zadat příkaz pro zobrazování Store prohlížeč bez plně kvalifikovaný obor názvů:  
>   
>  `using Microsoft.VisualStudio.Modeling.Diagnostics;`  
>   
>  `…`  
>   
>  `StoreViewer.Show(mystore);`  
  
 `Show` Metoda má několik přetížení. Instance úložišti nebo oddílu můžete zadat jako parametr.  
  
 Jako alternativu můžete vložit řádek kódu, který se zobrazí v prohlížeči Store kdekoli ve vašem kódu kde parametr, který můžete předat `Show` metoda je v oboru. Tato akce zobrazí prohlížeč Store, když se na řádek kódu provádí jako snímek obsah úložiště.  
  
### <a name="using-store-viewer"></a>Použití prohlížeče Store  
 Když se otevře prohlížeč Store nemodálním okně a Windows Forms se zobrazí, jak ukazuje následující obrázek.  
  
 ![](../modeling/media/storeviewer2.png "storeviewer2")  
Prohlížeč Store  
  
 Prohlížeč Store má tři podokna: levé, pravé horní části podokna a pravém dolním podokně. V levém podokně je stromové zobrazení typů v `DomainDataDirectory` člen úložiště. Pokud rozbalte uzel oddílu a klikněte na prvek elementu vlastnosti se zobrazí v pravém podokně. Pokud element je propojený s ostatními prvky, další prvky se zobrazí v podokně vpravo dole. Pokud dvakrát kliknete na prvek v pravém podokně se v levém podokně zvýrazní prvek.  
  
## <a name="see-also"></a>Viz také  
 [Navigace v modelu a aktualizace modelu v kódu programu](../modeling/navigating-and-updating-a-model-in-program-code.md)



