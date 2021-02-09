---
title: Balení informací o nasazení & v položkách projektu
description: Přidejte data o balení a nasazení v položkách projektu služby SharePoint pomocí vlastností funkcí, přijímačů funkcí, odkazů na výstup projektu a entit bezpečný ovládací prvek.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SafeControlEntries
- VS.SharePointTools.Project.ProjectOutputReference
- VS.SharePointTools.Project.FeatureProperties
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, safe controls
- project output references [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, feature properties
- SharePoint development in Visual Studio, project output references
- SharePoint development in Visual Studio, advanced packaging tools
- feature properties [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, feature receiver
- feature receiver [SharePoint development in Visual Studio]
- safe controls [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f05e2035338ea4c2d0e45bb9d135d618b938e4ca
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889535"
---
# <a name="provide-packaging-and-deployment-information-in-project-items"></a>Poskytnutí informací o balení a nasazení v položkách projektu
  Všechny položky projektu služby SharePoint v aplikaci [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] mají vlastnosti, které lze použít k poskytnutí dalších dat při nasazení projektu do služby SharePoint. Tyto vlastnosti jsou následující:

- Vlastnosti funkce

- Přijímače funkcí

- Odkazy na výstup projektu

- Položky bezpečného řízení

  Tyto vlastnosti se zobrazí v okně **vlastnosti** .

## <a name="feature-properties"></a>Vlastnosti funkce
 Pomocí vlastnosti **vlastnosti funkce** určete data, která funkce používá. Data vlastností funkcí jsou sada hodnot (uložené jako páry klíč/hodnota), která je součástí funkce při nasazení na SharePoint. Po nasazení funkce můžete získat přístup k hodnotám vlastností v kódu.

 Když přidáte hodnotu vlastnosti funkce do položky projektu, hodnota je přidána jako prvek v manifestu funkce položky. V projektu modelu připojení obchodních dat (BDC) se například vlastnost funkce ModelFileName zobrazí jako:

```xml
<Property Key="ModelFileName" Value="BdcModel1\BdcModel1.bdcm" />
```

 Po nastavení hodnoty vlastnosti funkce je přidána do souboru *. spdata* projektu jako element FeatureProperty –. Informace o přístupu k vlastnostem v SharePointu naleznete v tématu [Třída SPFeaturePropertyCollection](/previous-versions/office/sharepoint-server/ms461895(v=office.15)).

 Stejné hodnoty vlastností funkcí ze všech položek projektu jsou sloučeny společně v manifestu funkce. Pokud však dvě různé položky projektu určují stejný klíč vlastnosti funkce s nevyhovujícími hodnotami, dojde k chybě ověření.

 Chcete-li přidat vlastnosti funkce přímo do souboru funkce (*. funkce*), zavolejte [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] metodu Object Model služby SharePoint <xref:Microsoft.VisualStudio.SharePoint.Features.IPropertyCollection.Add%2A> . Pokud použijete tuto metodu, pamatujte na to, že stejné pravidlo pro přidání stejných hodnot vlastností funkcí ve vlastnostech funkce platí také pro vlastnosti přidané přímo do souboru funkce.

## <a name="feature-receiver"></a>Přijímač funkcí
 Přijímače funkcí jsou kód, který se spustí, když dojde k určitým událostem obsahujícím funkci položky projektu. Můžete například definovat přijímače funkcí, které se spouštějí při instalaci, aktivaci nebo upgradu funkce. Jedním ze způsobů, jak přidat přijímače funkcí, je přidat ho přímo do funkce, jak je popsáno v tématu [Návod: Přidání přijímačů událostí funkce](../sharepoint/walkthrough-add-feature-event-receivers.md). Dalším způsobem je odkazování na název třídy příjemce funkce a sestavení ve vlastnosti **přijímače funkce** .

### <a name="direct-method"></a>Direct – metoda
 Když přidáte přijímač funkcí přímo do funkce, je soubor kódu umístěn pod uzlem **funkce** v Průzkumník řešení. Při sestavování řešení služby SharePoint se kód zkompiluje do sestavení a nasadí se do služby SharePoint. Ve výchozím nastavení vlastnosti funkce **příjemce** a **Třída přijímače** odkazují na název a sestavení třídy.

### <a name="reference-method"></a>Reference – metoda
 Dalším způsobem, jak přidat přijímač funkcí, je pomocí vlastnosti **přijímač funkcí** položky projektu odkazovat na sestavení přijímače funkcí. Hodnota vlastnosti přijímače funkce má dvě podvlastnosti: název **sestavení** a **třídy**. Sestavení musí používat plně kvalifikovaný název "silného" a název třídy musí být úplný název typu. Další informace naleznete v tématu [sestavení se silným názvem](/previous-versions/dotnet/netframework-4.0/wd40t7ad(v=vs.100)). Po nasazení řešení do služby SharePoint funkce používá příjemce odkazované funkce ke zpracování událostí funkcí.

 V době sestavování řešení se hodnoty vlastností přijímače funkce v rámci funkce a jejích projektů sloučí dohromady, aby se nastavily atributy ReceiverAssembly a ReceiverClass elementu funkce v manifestu funkce souboru řešení služby SharePoint (*. wsp*). Proto pokud jsou zadány hodnoty vlastností název sestavení a třídy položky projektu a funkce, musí se shodovat hodnoty vlastností položky projektu a funkce. Pokud se hodnoty neshodují, zobrazí se chyba ověřování. Chcete-li, aby položka projektu odkazovala na jiné než takové sestavení příjemce funkce, přesuňte ho do jiné funkce.

 Pokud odkazujete na sestavení příjemce funkce, které ještě není na serveru, musíte do balíčku zahrnout taky samotný soubor sestavení. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nepřidá ho za vás. Při nasazení funkce je soubor sestavení zkopírován do [!INCLUDE[TLA#tla_gac](../sharepoint/includes/tlasharptla-gac-md.md)] složky systému nebo do složky bin ve fyzickém adresáři služby SharePoint. Další informace najdete v tématu Postupy: [Přidání a odebrání dalších sestavení](../sharepoint/how-to-add-and-remove-additional-assemblies.md).

 Další informace o přijímačích funkcí najdete v tématu [přijímač událostí funkcí](/previous-versions/office/developer/sharepoint-2007/bb862634(v=office.12)) a [události funkcí](/previous-versions/office/developer/sharepoint-2010/ms469501(v=office.14)).

## <a name="project-output-references"></a>Odkazy na výstup projektu
 Vlastnost výstupní odkazy projektu určuje závislost, jako je například sestavení, kterou musí vaše položka projektu spustit. Předpokládejme například, že vaše řešení má projekt BDC a projekt třídy. Pokud má projekt služby BDC závislost na sestavení, které je výstupem projektu třídy, můžete odkazovat na sestavení ve vlastnosti výstupních odkazů projektu projektu služby BDC. Po zabalení projektu služby BDC je závislé sestavení zahrnuto do balíčku.

 Odkazy na výstup projektu jsou obvykle sestavení, ale v některých případech (například projekty Silverlight) mohou být jiné typy souborů.

 Další informace najdete v tématu [Postup: Přidání odkazu na výstup projektu](../sharepoint/how-to-add-a-project-output-reference.md).

## <a name="safe-control-entries"></a>Položky bezpečného řízení
 SharePoint poskytuje bezpečnostní mechanismus, který se nazývá položky bezpečného řízení, aby omezil přístup nedůvěryhodných uživatelů na určité ovládací prvky. V rámci návrhu služba SharePoint umožňuje nedůvěryhodným uživatelům nahrávat a vytvářet stránky ASPX na SharePointovém serveru. Aby mohli tito uživatelé zabránit přidávání nezabezpečeného kódu na stránky ASPX, SharePoint omezuje přístup k *bezpečným ovládacím prvkům*. Bezpečné ovládací prvky jsou ovládací prvky ASPX a webové části označené jako zabezpečené a mohou být použity jakýmkoli uživatelem na webu. Další informace najdete v části [Krok 4: Přidání webové části do seznamu bezpečných ovládacích prvků](/previous-versions/office/developer/sharepoint-2007/ms581321(v=office.12)).

 Každá položka SharePointového projektu v aplikaci [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] má vlastnost nazvanou **položky bezpečného řízení** , které mají dvě logické podvlastnosti: **bezpečné** a **bezpečné proti skriptu**. Vlastnost Safe určuje, zda mohou nedůvěryhodní uživatelé přistupovat k ovládacímu prvku. Vlastnost Safe proti skriptu určuje, zda mohou nedůvěryhodní uživatelé zobrazovat a měnit vlastnosti ovládacího prvku.

 Položky bezpečného řízení jsou odkazovány na základě sestavení. Do sestavení projektu přidáte položky bezpečného řízení jeho zadáním do vlastnosti **položky bezpečného řízení** položky projektu. Můžete však také přidat položky bezpečného řízení do sestavení projektu prostřednictvím karty **Upřesnit** v **Návrháři balíčku** při přidání dalšího sestavení do balíčku. Další informace naleznete v tématu [Postupy: označení ovládacích prvků jako bezpečných ovládacích prvků](../sharepoint/how-to-mark-controls-as-safe-controls.md) nebo [registrace sestavení webové části jako bezpečného řízení](/previous-versions/office/developer/sharepoint2003/dd587360(v=office.11)).

### <a name="xml-entries-for-safe-controls"></a>Položky XML pro bezpečné ovládací prvky
 Když přidáte položku bezpečného řízení do položky projektu nebo do sestavení projektu, odkaz je zapsán do manifestu balíčku v následujícím formátu:

```xml
<Assemblies>
    <Assembly Location="<assembly name>.dll"
      DeploymentTarget="<'GlobalAssemblyCache' or 'WebApplication'">>
        <SafeControls>
            <SafeControl Assembly="<assembly name>.dll" Namespace=
              "<SharePoint project name>" Safe="<true/false>"
                TypeName="<control name>"
                SafeAgainstScript="<true/false>" />
        </SafeControls>
    </Assembly>
</Assemblies>
```

## <a name="see-also"></a>Viz také
- [Zabalení a nasazení řešení služby SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [Zahrnutí souborů do řešení pomocí modulů](../sharepoint/using-modules-to-include-files-in-the-solution.md)
- [Rozšiřování balení a nasazení služby SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
