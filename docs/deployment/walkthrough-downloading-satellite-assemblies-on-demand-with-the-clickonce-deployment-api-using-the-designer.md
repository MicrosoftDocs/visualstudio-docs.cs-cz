---
title: 'Návod: Stahování satelitních sestavení na vyžádání pomocí nasazení ClickOnce pomocí návrháře rozhraní API | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 79c5616a9233466c71ca036c4c0cb70d43649979
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2018
ms.locfileid: "39154856"
---
# <a name="walkthrough-download-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>Návod: Stahování satelitních sestavení na vyžádání pomocí nasazení ClickOnce pomocí návrháře rozhraní API
Aplikace Windows Forms lze nastavit pro více jazykových verzí pomocí satelitních sestavení. A *satelitní sestavení* je sestavení obsahující prostředky aplikací pro jazykovou verzi, než je výchozí jazykovou verzi aplikace.  
  
 Jak je popsáno v [lokalizace aplikací ClickOnce](../deployment/localizing-clickonce-applications.md), může obsahovat více satelitní sestavení pro více jazykových verzí v rámci stejného [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení. Ve výchozím nastavení [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] stáhne všechny satelitní sestavení ve vašem nasazení do klientského počítače, i když jednoho klienta, bude pravděpodobně vyžadovat jenom jeden satelitní sestavení.  
  
 Tento návod ukazuje, jak označit vaše satelitní sestavení jako volitelné a stáhnout pouze sestavení klientský počítač, musí mít nastavení aktuální jazykové verze.  
  
> [!NOTE]
>  Pro účely testování následující příklady kódu prostřednictvím kódu programu nastavit jazykovou verzi `ja-JP`. V části "Další kroky" dále v tomto tématu informace o tom, jak upravit tento kód pro produkční prostředí.  
  
### <a name="to-mark-satellite-assemblies-as-optional"></a>K označení satelitní sestavení jako volitelný  
  
1.  Sestavte projekt. Tím se vygeneruje satelitní sestavení pro všechny jazykové verze, které jsou k lokalizaci.  
  
2.  Klikněte pravým tlačítkem na název vašeho projektu v Průzkumníku řešení a klikněte na tlačítko **vlastnosti**.  
  
3.  Klikněte na tlačítko **publikovat** kartu a potom klikněte na tlačítko **soubory aplikace**.  
  
4.  Vyberte **zobrazit všechny soubory** zaškrtnutím políčka Zobrazit satelitní sestavení. Všechny satelitní sestavení ve výchozím nastavení, budou zahrnuty ve vašem nasazení a bude viditelný v tomto dialogovém.  
  
     Satelitní sestavení bude mít název ve tvaru  *\<isoCode > \ApplicationName.resources.dll*, kde \<isoCode > je ve formátu RFC 1766 identifikátor jazyka.  
  
5.  Klikněte na tlačítko **nový** v **skupina pro stažení** seznamu pro každý identifikátor jazyka. Po zobrazení výzvy pro název skupiny stažení, zadejte identifikátor jazyka. Například by pro japonské satelitní sestavení, zadejte název skupiny stažení `ja-JP`.  
  
6.  Zavřít **soubory aplikace** dialogové okno.  
  
### <a name="to-download-satellite-assemblies-on-demand-in-c"></a>Chcete-li stáhnout satelitních sestavení na vyžádání v jazyce C# 
  
1.  Otevřít *Program.cs* souboru. Pokud se tento soubor v Průzkumníku řešení, vyberte svůj projekt nezobrazí a na **projektu** nabídky, klikněte na tlačítko **zobrazit všechny soubory**.  
  
2.  Pomocí následujícího kódu ke stažení příslušného satelitního sestavení a spuštění aplikace.  
  
     [!code-csharp[ClickOnce.SatelliteAssemblies#1](../deployment/codesnippet/CSharp/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_1.cs)]  
  
### <a name="to-download-satellite-assemblies-on-demand-in-visual-basic"></a>Chcete-li stáhnout satelitních sestavení na vyžádání v jazyce Visual Basic  
  
1.  V **vlastnosti** okno pro aplikace, klikněte **aplikace** kartu.  
  
2.  V dolní části stránky karty, klikněte na tlačítko **zobrazení události aplikace**.  
  
3.  Přidejte následující importy do začátku *ApplicationEvents.VB* souboru.  
  
     [!code-vb[ClickOnce.SatelliteAssembliesVB#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_2.vb)]  
  
4.  Přidejte následující kód, který `MyApplication` třídy.  
  
     [!code-vb[ClickOnce.SatelliteAssembliesVB#2](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_3.vb)]  
  
## <a name="next-steps"></a>Další kroky  
 V produkčním prostředí, budete pravděpodobně muset odebrat řádek v příkladech kódu, které nastaví <xref:System.Threading.Thread.CurrentUICulture%2A> na určitou hodnotu, protože klientské počítače budou mít správnou hodnotu ve výchozím nastavení. Pokud vaše aplikace běží na počítači japonské klienta, například <xref:System.Threading.Thread.CurrentUICulture%2A> bude `ja-JP` ve výchozím nastavení. Nastavení programu je dobrým způsobem, jak testovat satelitní sestavení před nasazením aplikace.  
  
## <a name="see-also"></a>Viz také:  
 [Návod: Stahování satelitních sestavení na vyžádání pomocí rozhraní API nasazení ClickOnce](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)   
 [Lokalizace aplikací ClickOnce](../deployment/localizing-clickonce-applications.md)
