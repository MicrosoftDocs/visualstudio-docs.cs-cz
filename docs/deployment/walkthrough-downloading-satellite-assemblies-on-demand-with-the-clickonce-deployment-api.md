---
title: 'Návod: Stahování satelitních sestavení na vyžádání pomocí rozhraní API nasazení ClickOnce | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 506495f8be0b552f35bed0610e9fb43a77efb151
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49883026"
---
# <a name="walkthrough-download-satellite-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Návod: Stahování satelitních sestavení na vyžádání pomocí rozhraní API nasazení ClickOnce
Aplikace Windows Forms lze nastavit pro více jazykových verzí pomocí satelitních sestavení. A *satelitní sestavení* je sestavení obsahující prostředky aplikací pro jazykovou verzi, než je výchozí jazykovou verzi aplikace.  
  
 Jak je popsáno v [aplikací ClickOnce lokalizovat](../deployment/localizing-clickonce-applications.md), může obsahovat více satelitní sestavení pro více jazykových verzí v rámci stejného [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení. Ve výchozím nastavení [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] stáhne všechny satelitní sestavení ve vašem nasazení do klientského počítače, i když jednoho klienta, bude pravděpodobně vyžadovat jenom jeden satelitní sestavení.  
  
 Tento návod ukazuje, jak označit vaše satelitní sestavení jako volitelné a stáhnout pouze sestavení klientský počítač, musí mít nastavení aktuální jazykové verze. Následující postup používá nástroje, které jsou dostupné [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Můžete také provést tuto úlohu v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Viz také [návod: stahování satelitních sestavení na vyžádání pomocí nasazení ClickOnce pomocí návrháře rozhraní API](/previous-versions/visualstudio/visual-studio-2012/ms366788(v=vs.110)) nebo [návod: stahování satelitních sestavení na vyžádání pomocí rozhraní API nasazení ClickOnce Návrhář](/previous-versions/visualstudio/visual-studio-2013/ms366788(v=vs.120)).  
  
> [!NOTE]
>  Pro účely testování následující příklad kódu prostřednictvím kódu programu Nastaví jazykovou verzi na `ja-JP`. V části "Další kroky" dále v tomto tématu informace o tom, jak upravit tento kód pro produkční prostředí.  
  
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že víte, jak přidat lokalizované prostředky do vaší aplikace pomocí sady Visual Studio. Podrobné pokyny najdete v tématu [návod: lokalizace Windows forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100)).  
  
### <a name="to-download-satellite-assemblies-on-demand"></a>Chcete-li stáhnout satelitních sestavení na vyžádání  
  
1. Přidejte následující kód do vaší aplikace, které chcete povolit stahování satelitních sestavení na vyžádání.  
  
    [!code-csharp[ClickOnce.SatelliteAssembliesSDK#1](../deployment/codesnippet/CSharp/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]
    [!code-vb[ClickOnce.SatelliteAssembliesSDK#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]  
  
2. Generování satelitních sestavení pro vaši aplikaci s použitím [Resgen.exe (Generátor zdrojových souborů)](/dotnet/framework/tools/resgen-exe-resource-file-generator) nebo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
3. Generovat manifest aplikace, nebo otevřete existující manifest aplikace s použitím *MageUI.exe*. Další informace o tomto nástroji najdete v tématu [MageUI.exe (Manifest Generation and Editing Tool, grafický klient)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client).  
  
4. Klikněte na tlačítko **soubory** kartu.  
  
5. Klikněte na tlačítko **tlačítko se třemi tečkami** tlačítko (**...** ) a vyberte adresář obsahující sestavení vaší aplikace a soubory, včetně satelitní sestavení generována pomocí *Resgen.exe*. (Satelitní sestavení bude mít název ve tvaru  *\<isoCode > \ApplicationName.resources.dll*, kde \<isoCode > je identifikátor jazyka ve formátu RFC 1766.)  
  
6. Klikněte na tlačítko **naplnit** na přidání souborů do vašeho nasazení.  
  
7. Vyberte **volitelné** zaškrtávací políčko pro každé satelitní sestavení.  
  
8. Nastavte pole skupiny pro každou satelitní sestavení pro jeho identifikátor jazyka ISO. Například by pro japonské satelitní sestavení, zadejte název skupiny stažení `ja-JP`. To vám umožní kód, který jste přidali v kroku 1, chcete-li stáhnout příslušného satelitního sestavení, v závislosti na uživatele <xref:System.Threading.Thread.CurrentUICulture%2A> nastavení vlastnosti.  
  
## <a name="next-steps"></a>Další kroky  
 V produkčním prostředí, budete pravděpodobně muset odebrat řádek v příkladu kódu, který nastaví <xref:System.Threading.Thread.CurrentUICulture%2A> na určitou hodnotu, protože klientské počítače budou mít správnou hodnotu ve výchozím nastavení. Pokud vaše aplikace běží na počítači japonské klienta, například <xref:System.Threading.Thread.CurrentUICulture%2A> bude `ja-JP` ve výchozím nastavení. Pokud tuto hodnotu nastavíte prostřednictvím kódu programu je dobrým způsobem, jak testovat satelitní sestavení před nasazením aplikace.  
  
## <a name="see-also"></a>Viz také:  
 [Lokalizace aplikací ClickOnce](../deployment/localizing-clickonce-applications.md)