---
title: 'Návod: Stahování satelitních sestavení na vyžádání pomocí rozhraní API nasazení ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: a84de037661992d1ee185bea2a70db74dac5e618
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686357"
---
# <a name="walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Návod: Stahování satelitních sestavení na vyžádání pomocí rozhraní API nasazení ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Model Windows Forms aplikace lze nakonfigurovat pro více jazykových verzí prostřednictvím použití satelitních sestavení. *Satelitní sestavení* je sestavení, které obsahuje prostředky aplikace pro jinou jazykovou verzi, než je výchozí jazyková verze aplikace.  
  
 Jak je popsáno v tématu [lokalizace aplikací ClickOnce](../deployment/localizing-clickonce-applications.md), můžete zahrnout více satelitních sestavení pro více jazykových verzí v rámci stejného [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení. Ve výchozím nastavení [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] stáhne všechna satelitní sestavení v nasazení do klientského počítače, i když jeden klient bude pravděpodobně vyžadovat pouze jedno satelitní sestavení.  
  
 Tento návod ukazuje, jak označit vaše satelitní sestavení jako volitelné a stáhnout pouze sestavení, které klientský počítač potřebuje pro aktuální nastavení jazykové verze. Následující postup používá nástroje, které jsou k dispozici v nástroji [!INCLUDE[winsdklong](../includes/winsdklong-md.md)] . Tuto úlohu můžete provést také v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  Viz také [Návod: Stahování satelitních sestavení na vyžádání pomocí rozhraní API nasazení ClickOnce pomocí návrháře](https://msdn.microsoft.com/library/ms366788\(v=vs.110\)) nebo [návodu: Stahování satelitních sestavení na vyžádání pomocí rozhraní API nasazení ClickOnce pomocí návrháře](https://msdn.microsoft.com/library/ms366788\(v=vs.120\)).  
  
> [!NOTE]
> Pro účely testování následující příklad kódu programově nastaví jazykovou verzi na `ja-JP` . Informace o tom, jak upravit tento kód pro produkční prostředí, najdete v části Další kroky dále v tomto tématu.  
  
## <a name="prerequisites"></a>Požadavky  
 V tomto tématu se předpokládá, že víte, jak přidat lokalizované prostředky do aplikace pomocí sady Visual Studio. Podrobné pokyny najdete v tématu [Návod: lokalizace model Windows Forms](https://msdn.microsoft.com/library/vstudio/y99d1cd3\(v=vs.100\).aspx).  
  
### <a name="to-download-satellite-assemblies-on-demand"></a>Stažení satelitních sestavení na vyžádání  
  
1. Přidejte do aplikace následující kód, který umožní stahování satelitních sestavení na vyžádání.  
  
     [!code-csharp[ClickOnce.SatelliteAssembliesSDK#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesSDK/CS/Program.cs#1)]
     [!code-vb[ClickOnce.SatelliteAssembliesSDK#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesSDK/VB/Form1.vb#1)]  
  
2. Generujte satelitní sestavení pro vaši aplikaci pomocí [Resgen.exe (generátor zdrojových souborů)](https://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) nebo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
3. Vygenerujte manifest aplikace nebo otevřete existující manifest aplikace pomocí MageUI.exe. Další informace o tomto nástroji najdete v tématu [MageUI.exe (Manifest Generation and Editing Tool, grafický klient)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14).  
  
4. Klikněte na kartu **soubory** .  
  
5. Klikněte na tlačítko se **třemi tečkami** (**...**) a vyberte adresář obsahující všechna sestavení a soubory vaší aplikace, včetně satelitních sestavení, které jste vygenerovali pomocí Resgen.exe. (Satelitní sestavení bude mít název ve tvaru *isoCode*\ApplicationName.resources.dll, kde *isoCode* je identifikátor jazyka ve formátu RFC 1766.)  
  
6. Kliknutím na tlačítko **naplnit** přidejte soubory do nasazení.  
  
7. Zaškrtněte políčko **volitelné** pro každé satelitní sestavení.  
  
8. Nastavte pole Skupina pro každé satelitní sestavení na svůj identifikátor jazyka ISO. Například pro japonské satelitní sestavení byste měli zadat název skupiny pro stahování `ja-JP` . Tím se povolí kód, který jste přidali v kroku 1 ke stažení příslušného satelitního sestavení v závislosti na <xref:System.Threading.Thread.CurrentUICulture%2A> nastavení vlastnosti daného uživatele.  
  
## <a name="next-steps"></a>Další kroky  
 V produkčním prostředí bude pravděpodobně nutné odebrat řádek v příkladu kódu, který je nastaven <xref:System.Threading.Thread.CurrentUICulture%2A> na konkrétní hodnotu, protože klientské počítače budou mít ve výchozím nastavení nastavenou správnou hodnotu. Pokud vaše aplikace běží na japonském klientském počítači, například, <xref:System.Threading.Thread.CurrentUICulture%2A> bude `ja-JP` ve výchozím nastavení. Nastavení této hodnoty programově je dobrým způsobem, jak testovat satelitní sestavení před nasazením aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Lokalizace aplikací ClickOnce](../deployment/localizing-clickonce-applications.md)
