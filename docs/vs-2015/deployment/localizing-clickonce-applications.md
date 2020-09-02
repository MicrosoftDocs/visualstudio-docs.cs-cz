---
title: Lokalizace aplikací ClickOnce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- WPF, ClickOnce applications
- ClickOnce deployment, globalization
- deploying applications [ClickOnce], localizing ClickOnce applications
- localization, ClickOnce deployment
- ClickOnce deployment, download on-demand
- ClickOnce deployment, localization
- Windows Forms, ClickOnce applications
- console applications, ClickOnce applications
ms.assetid: c92b193b-054d-4923-834b-d4226a4c7a1a
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3c29bd6a58d510d98f2a08c96d0cd0bc774e197e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65680004"
---
# <a name="localizing-clickonce-applications"></a>Lokalizace aplikací ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lokalizace je proces zajištění vhodné aplikace pro konkrétní jazykovou verzi. Tento proces zahrnuje převod textu uživatelského rozhraní (UI) do jazyka specifického pro oblast, pomocí správného formátování data a měny, přizpůsobení velikosti ovládacích prvků ve formuláři a v případě potřeby zrcadlení ovládacích prvků v pravém rohu.  
  
 Lokalizace vaší aplikace má za následek vytvoření jednoho nebo více satelitních sestavení. Každé sestavení obsahuje řetězce uživatelského rozhraní, obrázky a další prostředky, které jsou specifické pro danou jazykovou verzi. (Hlavní spustitelný soubor vaší aplikace obsahuje řetězce pro výchozí jazykovou verzi vaší aplikace.)  
  
 V tomto tématu jsou popsány tři způsoby nasazení [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace pro jiné jazykové verze:  
  
- Zahrňte všechna satelitní sestavení v jednom nasazení.  
  
- Vygenerujte jedno nasazení pro každou jazykovou verzi s jedním satelitním sestavením zahrnutým do každého.  
  
- Stáhněte si satelitní sestavení na vyžádání.  
  
## <a name="including-all-satellite-assemblies-in-a-deployment"></a>Zahrnutí všech satelitních sestavení v nasazení  
 Namísto publikování více [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení můžete publikovat jedno [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení, které obsahuje všechna satelitní sestavení.  
  
 Tato metoda je výchozím nastavením v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Chcete-li použít tuto metodu v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , není nutné provádět žádnou další práci.  
  
 Chcete-li použít tuto metodu s MageUI.exe, je nutné nastavit jazykovou verzi vaší aplikace jako **neutrální** v MageUI.exe. Dále musíte do svého nasazení ručně zahrnout všechna satelitní sestavení. V MageUI.exe můžete přidat satelitní sestavení pomocí tlačítka **naplnit** na kartě **soubory** manifestu aplikace.  
  
 Výhodou tohoto přístupu je, že vytvoří jediné nasazení a zjednodušuje lokalizovaný scénář nasazení. V době běhu se použije příslušné satelitní sestavení v závislosti na výchozí jazykové verzi operačního systému Windows daného uživatele. Nevýhodou tohoto přístupu je, že stáhne všechna satelitní sestavení pokaždé, když je aplikace nainstalována nebo aktualizována v klientském počítači. Pokud má vaše aplikace velký počet řetězců nebo pokud vaši zákazníci mají pomalé připojení k síti, může tento proces ovlivnit výkon při aktualizaci aplikace.  
  
> [!NOTE]
> Tento přístup předpokládá, že vaše aplikace upravuje výšku, šířku a polohu ovládacích prvků automaticky pro přizpůsobení různých velikostí textových řetězců v různých jazykových verzích. Model Windows Forms obsahuje celou řadu ovládacích prvků a technologií, které vám umožní navrhnout formulář, aby bylo možné snadno lokalizovat, včetně <xref:System.Windows.Forms.FlowLayoutPanel> <xref:System.Windows.Forms.TableLayoutPanel> ovládacích prvků a a také <xref:System.Windows.Forms.Control.AutoSize%2A> vlastností.  Viz také [Postupy: podpora lokalizace na model Windows Forms pomocí AutoSize a ovládacího prvku TableLayoutPanel](https://msdn.microsoft.com/library/1zkt8b33\(v=vs.110\)).  
  
## <a name="generate-one-deployment-for-each-culture"></a>Generovat jedno nasazení pro každou jazykovou verzi  
 V této strategii nasazení vygenerujete více nasazení. V každém nasazení zahrnete pouze satelitní sestavení potřebné pro konkrétní jazykovou verzi a označíte nasazení jako specifické pro danou jazykovou verzi.  
  
 Chcete-li použít tuto metodu v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , nastavte vlastnost **jazyk publikování** na kartě **publikovat** na požadovanou oblast. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bude automaticky zahrnovat satelitní sestavení požadované pro vybranou oblast a vyloučí všechna ostatní satelitní sestavení z nasazení.  
  
 Stejnou věc můžete dosáhnout pomocí nástroje MageUI.exe v Microsoft [!INCLUDE[winsdklong](../includes/winsdklong-md.md)] . Použijte tlačítko **naplnit** na kartě **soubory** manifestu aplikace pro vyloučení všech ostatních satelitních sestavení z adresáře aplikace a pak nastavte pole **culture** na kartě **název** pro manifest nasazení v MageUI.exe. Tyto kroky nezahrnují pouze správné satelitní sestavení, ale také nastavují `language` atribut u `assemblyIdentity` prvku v manifestu nasazení na odpovídající jazykovou verzi.  
  
 Po publikování aplikace je nutné tento krok opakovat pro každou další jazykovou verzi, kterou vaše aplikace podporuje. Je nutné zajistit, aby každý manifest aplikace byl pokaždé publikován do jiného adresáře webového serveru nebo sdílené složky souborů, protože každý manifest aplikace bude odkazovat na jiné satelitní sestavení a každý manifest nasazení bude mít pro atribut jinou hodnotu `language` .  
  
## <a name="downloading-satellite-assemblies-on-demand"></a>Stahování satelitních sestavení na vyžádání  
 Pokud se rozhodnete zahrnout všechna satelitní sestavení v jednom nasazení, můžete zvýšit výkon pomocí stahování na vyžádání, což vám umožní označit sestavení jako volitelné. Označená sestavení nebudou stažena při instalaci nebo aktualizaci aplikace. Sestavení můžete nainstalovat, když je potřebujete, voláním <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> metody <xref:System.Deployment.Application.ApplicationDeployment> třídy.  
  
 Stahování satelitních sestavení na vyžádání se mírně liší od stahování jiných typů sestavení na vyžádání. Další informace a příklady kódu pro povolení tohoto scénáře pomocí [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] nástrojů pro [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] naleznete v tématu [Návod: Stahování satelitních sestavení na vyžádání pomocí rozhraní API nasazení ClickOnce](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md).  
  
 Tento scénář můžete také povolit v nástroji [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  Viz také [Návod: Stahování satelitních sestavení na vyžádání pomocí rozhraní API nasazení ClickOnce pomocí návrháře](https://msdn.microsoft.com/library/ms366788\(v=vs.110\)) nebo [návodu: Stahování satelitních sestavení na vyžádání pomocí rozhraní API nasazení ClickOnce pomocí návrháře](https://msdn.microsoft.com/library/ms366788\(v=vs.120\)).  
  
## <a name="testing-localized-clickonce-applications-before-deployment"></a>Testování lokalizovaných aplikací ClickOnce před nasazením  
 Satelitní sestavení bude použito pro model Windows Forms aplikaci pouze v případě, že <xref:System.Threading.Thread.CurrentUICulture%2A> vlastnost pro hlavní vlákno aplikace je nastavena na jazykovou verzi satelitního sestavení. Zákazníci na místních trzích budou pravděpodobně mít již spuštěnou lokalizovanou verzi systému Windows s jejich jazykovou verzí nastavenou na odpovídající výchozí hodnotu.  
  
 Máte tři možnosti pro testování lokalizovaných nasazení před zpřístupněním vaší aplikace zákazníkům:  
  
- Aplikaci můžete spustit [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] v příslušných lokalizovaných verzích systému Windows.  
  
- Vlastnost můžete nastavit <xref:System.Threading.Thread.CurrentUICulture%2A> programově v aplikaci. (Tuto vlastnost je nutné nastavit před voláním <xref:System.Windows.Forms.Application.Run%2A> metody.)  
  
## <a name="see-also"></a>Viz také  
 [\<assemblyIdentity> Objekt](../deployment/assemblyidentity-element-clickonce-deployment.md)   
 [ClickOnce – zabezpečení a nasazení](../deployment/clickonce-security-and-deployment.md)   
 [Globalizace Windows Forms](https://msdn.microsoft.com/library/72f6cd92-83be-45ec-aa37-9cb8e3ebc3c5)
