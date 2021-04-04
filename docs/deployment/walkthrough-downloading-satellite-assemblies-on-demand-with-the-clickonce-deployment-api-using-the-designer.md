---
title: Stažení satelitního sestavení na vyžádání pomocí ClickOnce designeru
description: Naučte se, jak označit satelitní sestavení jako volitelné pomocí návrháře a stáhnout pouze sestavení, které klientský počítač potřebuje pro aktuální nastavení jazykové verze.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9e9166dbd3d6cd7ba4500e2390bd611a31bcee7b
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216875"
---
# <a name="walkthrough-download-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>Návod: Stahování satelitních sestavení na vyžádání pomocí rozhraní API nasazení ClickOnce pomocí návrháře
Model Windows Forms aplikace lze nakonfigurovat pro více jazykových verzí prostřednictvím použití satelitních sestavení. *Satelitní sestavení* je sestavení, které obsahuje prostředky aplikace pro jinou jazykovou verzi, než je výchozí jazyková verze aplikace.

 Jak je popsáno v tématu [lokalizace aplikací ClickOnce](../deployment/localizing-clickonce-applications.md), můžete zahrnout více satelitních sestavení pro více jazykových verzí v rámci stejného [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení. Ve výchozím nastavení [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] stáhne všechna satelitní sestavení v nasazení do klientského počítače, i když jeden klient bude pravděpodobně vyžadovat pouze jedno satelitní sestavení.

 Tento návod ukazuje, jak označit vaše satelitní sestavení jako volitelné a stáhnout pouze sestavení, které klientský počítač potřebuje pro aktuální nastavení jazykové verze.

> [!NOTE]
> Pro účely testování následující příklady kódu programově nastaví jazykovou verzi na `ja-JP` . Informace o tom, jak upravit tento kód pro produkční prostředí, najdete v části Další kroky dále v tomto tématu.

### <a name="to-mark-satellite-assemblies-as-optional"></a>Označení satelitních sestavení jako volitelné

1. Sestavte projekt. Tím dojde k vygenerování satelitních sestavení pro všechny jazykové verze, které jsou lokalizovány.

2. V Průzkumník řešení klikněte pravým tlačítkem myši na název projektu a klikněte na **vlastnosti**.

3. Klikněte na kartu **publikovat** a pak klikněte na **soubory aplikace**.

4. Zaškrtněte políčko **Zobrazit všechny soubory** , chcete-li zobrazit satelitní sestavení. Ve výchozím nastavení budou všechna satelitní sestavení obsažena v nasazení a budou viditelná v tomto dialogovém okně.

     Satelitní sestavení bude mít název ve tvaru *\<isoCode>\ApplicationName.resources.dll*, kde \<isoCode> je identifikátor jazyka ve formátu RFC 1766.

5. V seznamu skupin pro **stažení** jednotlivých identifikátorů jazyka klikněte na **Nový** . Po zobrazení výzvy k zadání názvu skupiny pro stahování zadejte identifikátor jazyka. Například pro japonské satelitní sestavení byste měli zadat název skupiny pro stahování `ja-JP` .

6. Zavřete dialogové okno **soubory aplikace** .

### <a name="to-download-satellite-assemblies-on-demand-in-c"></a>Stažení satelitních sestavení na vyžádání v jazyce C\#

1. Otevřete soubor *program. cs* . Pokud tento soubor v Průzkumník řešení nevidíte, vyberte projekt a v nabídce **projekt** klikněte na **Zobrazit všechny soubory**.

2. Pomocí následujícího kódu Stáhněte příslušné satelitní sestavení a spusťte aplikaci.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/ClickOnce.SatelliteAssemblies/CS/Program.cs" id="Snippet1":::

### <a name="to-download-satellite-assemblies-on-demand-in-visual-basic"></a>Stažení satelitních sestavení na vyžádání v Visual Basic

1. V okně **vlastnosti** aplikace klikněte na kartu **aplikace** .

2. V dolní části stránky karty klikněte na **Zobrazit události aplikace**.

3. Přidejte následující importy na začátek souboru *ApplicationEvents. vb* .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesVB/VB/ApplicationEvents.vb" id="Snippet1":::

4. Do třídy `MyApplication` přidejte následující kód.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesVB/VB/ApplicationEvents.vb" id="Snippet2":::

## <a name="next-steps"></a>Další kroky
 V produkčním prostředí bude pravděpodobně nutné odebrat řádek v příkladech kódu, který je nastaven <xref:System.Threading.Thread.CurrentUICulture%2A> na určitou hodnotu, protože klientské počítače budou mít ve výchozím nastavení nastavenou správnou hodnotu. Pokud vaše aplikace běží na japonském klientském počítači, například, <xref:System.Threading.Thread.CurrentUICulture%2A> bude `ja-JP` ve výchozím nastavení. Jeho nastavení programově je dobrým způsobem, jak testovat satelitní sestavení před nasazením aplikace.

## <a name="see-also"></a>Viz také
- [Návod: Stahování satelitních sestavení na vyžádání pomocí rozhraní API nasazení ClickOnce](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)
- [Lokalizace aplikací ClickOnce](../deployment/localizing-clickonce-applications.md)
