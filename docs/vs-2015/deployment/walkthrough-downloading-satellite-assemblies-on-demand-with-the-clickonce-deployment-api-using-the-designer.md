---
title: 'Návod: Stahování satelitních sestavení na vyžádání pomocí nasazení ClickOnce pomocí návrháře rozhraní API | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows Forms, globalization
- ClickOnce deployment, globalization
- localization, Windows Forms
- ClickOnce, on-demand download
- Windows Forms, localization
- ClickOnce deployment, localization
- walkthroughs, localization
ms.assetid: 82b85a47-b223-4221-a17c-38a52c3fb6e2
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 5ca86e2ed1a05c8e325a99686281db3a7cf8f56e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49306225"
---
# <a name="walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>Návod: Stahování satelitních sestavení na vyžádání pomocí rozhraní API nasazení ClickOnce pomocí Návrháře
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aplikace Windows Forms lze nastavit pro více jazykových verzí pomocí satelitních sestavení. A *satelitní sestavení* je sestavení obsahující prostředky aplikací pro jazykovou verzi, než je výchozí jazykovou verzi aplikace.  
  
 Jak je popsáno v [lokalizace aplikací ClickOnce](../deployment/localizing-clickonce-applications.md), může obsahovat více satelitní sestavení pro více jazykových verzí v rámci stejného [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení. Ve výchozím nastavení [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] stáhne všechny satelitní sestavení ve vašem nasazení do klientského počítače, i když jednoho klienta, bude pravděpodobně vyžadovat jenom jeden satelitní sestavení.  
  
 Tento návod ukazuje, jak označit vaše satelitní sestavení jako volitelné a stáhnout pouze sestavení klientský počítač, musí mít nastavení aktuální jazykové verze.  
  
> [!NOTE]
>  Pro účely testování následující příklady kódu prostřednictvím kódu programu nastavit jazykovou verzi `ja-JP`. V části "Další kroky" dále v tomto tématu informace o tom, jak upravit tento kód pro produkční prostředí.  
  
### <a name="to-mark-satellite-assemblies-as-optional"></a>K označení satelitní sestavení jako volitelný  
  
1.  Sestavte projekt. Tím se vygeneruje satelitní sestavení pro všechny jazykové verze, které jsou k lokalizaci.  
  
2.  Klikněte pravým tlačítkem na název vašeho projektu v Průzkumníku řešení a klikněte na tlačítko **vlastnosti**.  
  
3.  Klikněte na tlačítko **publikovat** kartu a potom klikněte na tlačítko **soubory aplikace**.  
  
4.  Vyberte **zobrazit všechny soubory** zaškrtnutím políčka Zobrazit satelitní sestavení. Všechny satelitní sestavení ve výchozím nastavení, budou zahrnuty ve vašem nasazení a bude viditelný v tomto dialogovém.  
  
     Satelitní sestavení bude mít název ve tvaru *isoCode*\ApplicationName.resources.dll, kde *isoCode* je ve formátu RFC 1766 identifikátor jazyka.  
  
5.  Klikněte na tlačítko **nové...**  v **skupina pro stažení** seznamu pro každý identifikátor jazyka. Po zobrazení výzvy pro název skupiny stažení, zadejte identifikátor jazyka. Například by pro japonské satelitní sestavení, zadejte název skupiny stažení `ja-JP`.  
  
6.  Zavřít **soubory aplikace** dialogové okno.  
  
### <a name="to-download-satellite-assemblies-on-demand-in-c"></a>Chcete-li stáhnout satelitních sestavení na vyžádání v jazyce C#  
  
1.  Otevřete soubor Program.cs. Pokud se tento soubor v Průzkumníku řešení, vyberte svůj projekt nezobrazí a na **projektu** nabídky, klikněte na tlačítko **zobrazit všechny soubory**.  
  
2.  Pomocí následujícího kódu ke stažení příslušného satelitního sestavení a spuštění aplikace.  
  
     [!code-csharp[ClickOnce.SatelliteAssemblies#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnce.SatelliteAssemblies/CS/Program.cs#1)]  
  
### <a name="to-download-satellite-assemblies-on-demand-in-visual-basic"></a>Chcete-li stáhnout satelitních sestavení na vyžádání v jazyce Visual Basic  
  
1.  V **vlastnosti** okno pro aplikace, klikněte **aplikace** kartu.  
  
2.  V dolní části stránky karty, klikněte na tlačítko **zobrazení události aplikace**.  
  
3.  Na začátek souboru ApplicationEvents.VB přidejte následující importy.  
  
     [!code-vb[ClickOnce.SatelliteAssembliesVB#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesVB/VB/ApplicationEvents.vb#1)]  
  
4.  Přidejte následující kód, který `MyApplication` třídy.  
  
     [!code-vb[ClickOnce.SatelliteAssembliesVB#2](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesVB/VB/ApplicationEvents.vb#2)]  
  
## <a name="next-steps"></a>Další kroky  
 V produkčním prostředí, budete pravděpodobně muset odebrat řádek v příkladech kódu, které nastaví <xref:System.Threading.Thread.CurrentUICulture%2A> na určitou hodnotu, protože klientské počítače budou mít správnou hodnotu ve výchozím nastavení. Pokud vaše aplikace běží na počítači japonské klienta, například <xref:System.Threading.Thread.CurrentUICulture%2A> bude `ja-JP` ve výchozím nastavení. Nastavení programu je dobrým způsobem, jak testovat satelitní sestavení před nasazením aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Stahování satelitních sestavení na vyžádání pomocí rozhraní API nasazení ClickOnce](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)   
 [Lokalizace aplikací ClickOnce](../deployment/localizing-clickonce-applications.md)



