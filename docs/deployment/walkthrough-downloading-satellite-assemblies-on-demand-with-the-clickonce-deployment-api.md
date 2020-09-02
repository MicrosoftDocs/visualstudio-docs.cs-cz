---
title: Stažení satelitního sestavení na vyžádání pomocí rozhraní API nasazení ClickOnce
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 34cde3a2444525e48455e445894fd5ab1c66fab8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "66262971"
---
# <a name="walkthrough-download-satellite-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Návod: Stahování satelitních sestavení na vyžádání pomocí rozhraní API nasazení ClickOnce
Model Windows Forms aplikace lze nakonfigurovat pro více jazykových verzí prostřednictvím použití satelitních sestavení. *Satelitní sestavení* je sestavení, které obsahuje prostředky aplikace pro jinou jazykovou verzi, než je výchozí jazyková verze aplikace.

 Jak je popsáno v tématu [lokalizace aplikací ClickOnce](../deployment/localizing-clickonce-applications.md), můžete zahrnout více satelitních sestavení pro více jazykových verzí v rámci stejného [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení. Ve výchozím nastavení [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] stáhne všechna satelitní sestavení v nasazení do klientského počítače, i když jeden klient bude pravděpodobně vyžadovat pouze jedno satelitní sestavení.

 Tento návod ukazuje, jak označit vaše satelitní sestavení jako volitelné a stáhnout pouze sestavení, které klientský počítač potřebuje pro aktuální nastavení jazykové verze. Následující postup používá nástroje, které jsou k dispozici v nástroji [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] . Tuto úlohu můžete provést také v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  Viz také [Návod: Stahování satelitních sestavení na vyžádání pomocí rozhraní API nasazení ClickOnce pomocí návrháře](/previous-versions/visualstudio/visual-studio-2012/ms366788(v=vs.110)) nebo [návodu: stažení satelitních sestavení na vyžádání pomocí rozhraní API nasazení ClickOnce pomocí návrháře](/previous-versions/visualstudio/visual-studio-2013/ms366788(v=vs.120)).

> [!NOTE]
> Pro účely testování následující příklad kódu programově nastaví jazykovou verzi na `ja-JP` . Informace o tom, jak upravit tento kód pro produkční prostředí, najdete v části Další kroky dále v tomto tématu.

## <a name="prerequisites"></a>Předpoklady
 V tomto tématu se předpokládá, že víte, jak přidat lokalizované prostředky do aplikace pomocí sady Visual Studio. Podrobné pokyny najdete v tématu [Návod: lokalizace modelu Windows Forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100)).

### <a name="to-download-satellite-assemblies-on-demand"></a>Stažení satelitních sestavení na vyžádání

1. Přidejte do aplikace následující kód, který umožní stahování satelitních sestavení na vyžádání.

    [!code-csharp[ClickOnce.SatelliteAssembliesSDK#1](../deployment/codesnippet/CSharp/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]
    [!code-vb[ClickOnce.SatelliteAssembliesSDK#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]

2. Generujte satelitní sestavení pro vaši aplikaci pomocí [Resgen.exe (generátor zdrojových souborů)](/dotnet/framework/tools/resgen-exe-resource-file-generator) nebo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

3. Vygenerujte manifest aplikace nebo otevřete existující manifest aplikace pomocí *MageUI.exe*. Další informace o tomto nástroji najdete v tématu [MageUI.exe (Manifest Generation and Editing Tool, grafický klient)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client).

4. Klikněte na kartu **soubory** .

5. Klikněte na tlačítko se **třemi tečkami** (**...**) a vyberte adresář obsahující všechna sestavení a soubory vaší aplikace, včetně satelitních sestavení, které jste vygenerovali pomocí *Resgen.exe*. (Satelitní sestavení bude mít název ve tvaru * \<isoCode>\ApplicationName.resources.dll*, kde \<isoCode> je identifikátor jazyka ve formátu RFC 1766.)

6. Kliknutím na tlačítko **naplnit** přidejte soubory do nasazení.

7. Zaškrtněte políčko **volitelné** pro každé satelitní sestavení.

8. Nastavte pole Skupina pro každé satelitní sestavení na svůj identifikátor jazyka ISO. Například pro japonské satelitní sestavení byste měli zadat název skupiny pro stahování `ja-JP` . Tím se povolí kód, který jste přidali v kroku 1 ke stažení příslušného satelitního sestavení v závislosti na <xref:System.Threading.Thread.CurrentUICulture%2A> nastavení vlastnosti daného uživatele.

## <a name="next-steps"></a>Další kroky
 V produkčním prostředí bude pravděpodobně nutné odebrat řádek v příkladu kódu, který je nastaven <xref:System.Threading.Thread.CurrentUICulture%2A> na konkrétní hodnotu, protože klientské počítače budou mít ve výchozím nastavení nastavenou správnou hodnotu. Pokud vaše aplikace běží na japonském klientském počítači, například, <xref:System.Threading.Thread.CurrentUICulture%2A> bude `ja-JP` ve výchozím nastavení. Nastavení této hodnoty programově je dobrým způsobem, jak testovat satelitní sestavení před nasazením aplikace.

## <a name="see-also"></a>Viz také
- [Lokalizace aplikací ClickOnce](../deployment/localizing-clickonce-applications.md)
