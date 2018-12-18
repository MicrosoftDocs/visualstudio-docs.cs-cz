---
title: 'Návod: Stahování satelitních sestavení na vyžádání pomocí rozhraní API nasazení ClickOnce | Dokumentace Microsoftu'
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
- ClickOnce deployment, globalization
- localization, Windows Forms
- Windows Forms, localization
- globalization, ClickOnce
- satellite assemblies, ClickOnce
- ClickOnce deployment, on-demand download
- localization, ClickOnce deployment
- ClickOnce deployment, localization
ms.assetid: fdaa553f-a27e-44eb-a4e2-08c122105a87
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 6e6de316fd0ff66e0815da7fa935d21e23a8285e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49306329"
---
# <a name="walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Návod: Stahování satelitních sestavení na vyžádání pomocí rozhraní API nasazení ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aplikace Windows Forms lze nastavit pro více jazykových verzí pomocí satelitních sestavení. A *satelitní sestavení* je sestavení obsahující prostředky aplikací pro jazykovou verzi, než je výchozí jazykovou verzi aplikace.  
  
 Jak je popsáno v [lokalizace aplikací ClickOnce](../deployment/localizing-clickonce-applications.md), může obsahovat více satelitní sestavení pro více jazykových verzí v rámci stejného [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení. Ve výchozím nastavení [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] stáhne všechny satelitní sestavení ve vašem nasazení do klientského počítače, i když jednoho klienta, bude pravděpodobně vyžadovat jenom jeden satelitní sestavení.  
  
 Tento návod ukazuje, jak označit vaše satelitní sestavení jako volitelné a stáhnout pouze sestavení klientský počítač, musí mít nastavení aktuální jazykové verze. Následující postup používá nástroje, které jsou dostupné [!INCLUDE[winsdklong](../includes/winsdklong-md.md)]. Můžete také provést tuto úlohu v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  Viz také [návod: stahování satelitních sestavení na vyžádání pomocí technologie ClickOnce pomocí rozhraní API nasazení návrháře](http://msdn.microsoft.com/library/ms366788\(v=vs.110\)) nebo [návod: stahování satelitních sestavení na vyžádání pomocí rozhraní API nasazení ClickOnce Pomocí návrháře](http://msdn.microsoft.com/library/ms366788\(v=vs.120\)).  
  
> [!NOTE]
>  Pro účely testování následující příklad kódu prostřednictvím kódu programu Nastaví jazykovou verzi na `ja-JP`. V části "Další kroky" dále v tomto tématu informace o tom, jak upravit tento kód pro produkční prostředí.  
  
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že víte, jak přidat lokalizované prostředky do vaší aplikace pomocí sady Visual Studio. Podrobné pokyny najdete v tématu [návod: lokalizace Windows Forms](https://msdn.microsoft.com/library/vstudio/y99d1cd3\(v=vs.100\).aspx).  
  
### <a name="to-download-satellite-assemblies-on-demand"></a>Chcete-li stáhnout satelitních sestavení na vyžádání  
  
1.  Přidejte následující kód do vaší aplikace, které chcete povolit stahování satelitních sestavení na vyžádání.  
  
     [!code-csharp[ClickOnce.SatelliteAssembliesSDK#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesSDK/CS/Program.cs#1)]
     [!code-vb[ClickOnce.SatelliteAssembliesSDK#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesSDK/VB/Form1.vb#1)]  
  
2.  Generování satelitních sestavení pro vaši aplikaci s použitím [Resgen.exe (Generátor zdrojových souborů)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) nebo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
3.  Generovat manifest aplikace, nebo otevřete existující manifest aplikace s použitím MageUI.exe. Další informace o tomto nástroji najdete v tématu [MageUI.exe (Manifest Generation and Editing Tool, grafický klient)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14).  
  
4.  Klikněte na tlačítko **soubory** kartu.  
  
5.  Klikněte na tlačítko **tlačítko se třemi tečkami** tlačítko (**...** ) a vyberte adresáře, který obsahuje všechny soubory, včetně satelitní sestavení, který jste vygenerovali pomocí Resgen.exe a sestavení vaší aplikace. (Satelitní sestavení bude mít název ve tvaru *isoCode*\ApplicationName.resources.dll, kde *isoCode* je identifikátor jazyka ve formátu RFC 1766.)  
  
6.  Klikněte na tlačítko **naplnit** na přidání souborů do vašeho nasazení.  
  
7.  Vyberte **volitelné** zaškrtávací políčko pro každé satelitní sestavení.  
  
8.  Nastavte pole skupiny pro každou satelitní sestavení pro jeho identifikátor jazyka ISO. Například by pro japonské satelitní sestavení, zadejte název skupiny stažení `ja-JP`. To vám umožní kód, který jste přidali v kroku 1, chcete-li stáhnout příslušného satelitního sestavení, v závislosti na uživatele <xref:System.Threading.Thread.CurrentUICulture%2A> nastavení vlastnosti.  
  
## <a name="next-steps"></a>Další kroky  
 V produkčním prostředí, budete pravděpodobně muset odebrat řádek v příkladu kódu, který nastaví <xref:System.Threading.Thread.CurrentUICulture%2A> na určitou hodnotu, protože klientské počítače budou mít správnou hodnotu ve výchozím nastavení. Pokud vaše aplikace běží na počítači japonské klienta, například <xref:System.Threading.Thread.CurrentUICulture%2A> bude `ja-JP` ve výchozím nastavení. Pokud tuto hodnotu nastavíte prostřednictvím kódu programu je dobrým způsobem, jak testovat satelitní sestavení před nasazením aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Lokalizace aplikací ClickOnce](../deployment/localizing-clickonce-applications.md)



