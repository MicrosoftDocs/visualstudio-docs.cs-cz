---
title: Lokalizace řešení služby SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
f1_keywords:
- VS.SharePointTools.Project.GlobalAndFeatureResource
- VS.SharePoint.Project.AddResourceDialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- globalizing [SharePoint development in Visual Studio]
- localizing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0a7b04ab1f77eba15f2bc617f89514a8d0952674
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "86017140"
---
# <a name="localize-sharepoint-solutions"></a>Lokalizace řešení služby SharePoint

  Proces přípravy aplikací, aby je bylo možné používat po celém světě, se označuje jako lokalizace. Lokalizace překládá prostředky na konkrétní jazykovou verzi. Další informace najdete v tématu [globalizace a lokalizace aplikací](../ide/globalizing-and-localizing-applications.md). Toto téma poskytuje přehled o lokalizaci řešení služby SharePoint.

 Chcete-li lokalizovat řešení, odeberte pevně kódované řetězce z kódu a abstrakce je do souborů prostředků. Soubor prostředků je [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] soubor založený na příponě *. resx* . Soubor prostředků obsahuje přeložené verze řetězců používané ve vašem řešení. Další informace najdete v tématu [prostředky v aplikacích](/previous-versions/dotnet/netframework-4.0/f45fce5x(v=vs.100)).

> [!NOTE]
> Přidejte pouze řetězcové prostředky do souborů prostředků řešení služby SharePoint. I když editor prostředků umožňuje přidat neřetězcové prostředky, neřetězcové prostředky nejsou nasazeny do služby SharePoint.

## <a name="resource-files"></a>Soubory prostředků
 Existují tři typy souborů prostředků: výchozí, jazykově neutrální a specifické pro jazyk.

|Typ souboru prostředků|Popis|
|------------------------|-----------------|
|Výchozí|Také označované jako záložní prostředek, výchozí soubory prostředků obsahují řetězce lokalizované pro výchozí jazykovou verzi, například angličtinu. Používají se, pokud nelze najít žádné lokalizované soubory prostředků pro zadaný jazyk. Výchozí prostředky nemají samostatné soubory, jsou uloženy v sestavení hlavní aplikace.|
|Jazykově neutrální|Soubor prostředků obsahující řetězce lokalizované pro jazyk, ale ne specifickou jazykovou verzi. Například "fr" pro francouzštinu.|
|Pro jednotlivé jazyky|Soubor prostředků obsahující řetězce lokalizované pro jazyk a jazykovou verzi. Například "fr-CA" pro kanadskou francouzštinu.|

 Další informace najdete v tématu [Hierarchická organizace prostředků k lokalizaci](../ide/globalizing-and-localizing-applications.md).

 Chcete-li určit výchozí soubory prostředků v projektech služby SharePoint, které vyvíjíte v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , zvolte **neutrální jazyk (neutrální země)** v seznamu jazykové verze dialogového okna **Přidat prostředek** při přidání souboru prostředků.

## <a name="localize-visual-studio-sharepoint-solutions"></a>Lokalizace řešení služby SharePoint v aplikaci Visual Studio
 Při lokalizaci řešení byste měli vzít v úvahu všechny textové informace, které vaše řešení zobrazuje uživatelům. Informační zprávy, chybové zprávy a [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] řetězce je nutné přeložit a tyto překlady umístit do souborů prostředků.

 Každý řetězec v souboru prostředků má jedinečný identifikátor. V každém souboru prostředků použijte stejný identifikátor pro přeložený řetězec. Například pokud "řetězec1" je identifikátor prvního řetězce ve výchozím souboru prostředků, použijte stejný identifikátor jako první řetězec v souborech prostředků specifických pro jazyk.

 Existují tři oblasti, které obvykle lokalizacete v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aplikacích služby SharePoint: funkce, kód stránky ASPX a kód. Pro účely ilustrace se v následujících částech předpokládá, že máte řešení služby SharePoint, které chcete lokalizovat do němčiny a japonštiny. Výchozím jazykem je angličtina.

### <a name="localize-features"></a>Lokalizace funkcí
 Chcete-li lokalizovat funkci, je nutné nahradit pevně zakódovaný název a popis funkce výrazem, který odkazuje na přeložený název a řetězec v lokalizovaném souboru prostředků. Tuto změnu provedete v **Návrháři funkcí** v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Další informace naleznete v tématu [How to: Lokalizace funkce](../sharepoint/how-to-localize-a-feature.md).

 Chcete-li lokalizovat anglickou funkci do němčiny a japonštiny, přidejte tři položky projektu soubor prostředků do projektu: jeden pro angličtinu, jeden pro němčinu a jeden pro japonštinu. Soubory prostředků funkce nelze použít k lokalizaci kódu ASPX nebo kódu; pro ně jsou vyžadovány samostatné soubory prostředků.

 Po vytvoření souborů prostředků funkce přidejte do nich přeložené řetězce. Přístup k lokalizovaným řetězcům pomocí výrazu v následujícím formátu:

```aspx-csharp
$Resources:String ID
```

 Prostředky funkcí v portálu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] jsou vždy pojmenovány prostředky. Pokud vyberete jiný jazyk než neutrální jazyk, [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] přidá se k názvu souboru prostředků jazyková verze. Například pokud přidáte soubor prostředků funkce invariantního jazyka (výchozí), nazývá se *Resources. resx*. Pokud přidáte prostředek funkce specifický pro jazyk tak, že vyberete jazykovou verzi japonštiny (Japonsko), soubor se nazývá *Resources. ja-JP. resx*. Názvy souborů prostředků funkcí jsou automaticky přiřazeny a nelze je změnit.

 Rozsah prostředků funkcí je místní pro funkci, ke které se přidávají. Chcete-li vytvořit prostředky, které mohou být použity jakýmkoli souborem funkcí nebo prvků v řešení, přidejte položku projektu **globálních prostředků** namísto souboru prostředků funkce. Položka projektu **globální soubor prostředků** je umístěna ve složce **2010** v části **SharePoint** v dialogovém okně **Přidat novou položku** . Soubory globálních prostředků se nasazují do složky \Resources v kořenové složce SharePointu.

### <a name="localize-aspx-page-markup"></a>Kód stránky ASPX pro lokalizaci
 Chcete-li lokalizovat [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] stránky, přidejte do projektu tři položky soubor prostředků projektu: jeden pro angličtinu, jeden pro němčinu a jeden pro japonštinu. Pokud nemusíte lokalizovat kód spolu se značkou, můžete místo toho přidat globální soubory prostředků.

 Zadejte název souboru prostředků výchozího jazyka. Poskytněte lokalizované soubory prostředků se stejným názvem, který je připojený k jazykově specifické jazykové verzi [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] . Například *MyAppResources.de-de. resx* pro němčinu a *MyAppResources. ja-JP. resx* pro japonštinu.

 Nastavte vlastnost **typ nasazení** každého souboru prostředků na **AppGlobalResource**. To způsobí, že se soubory prostředků nasadí do složky App_GlobalResources, kde jsou k dispozici pro všechny stránky ASPX a ovládací prvky v řešení. Složka App_GlobalResources se nachází v C:\inetpub\wwwroot\wss\VirtualDirectories \\<číslo portu \> \ App_GlobalResources.

> [!NOTE]
> Použijete-li neglobální soubory prostředků, přesuňte je do složky položky projektu, čímž povolíte vlastnost typ nasazení a další vlastnosti specifické pro službu SharePoint.

 Soubory prostředků značek ASPX lze také použít k lokalizaci kódu. Pokud používáte prostředky k lokalizaci kódu kromě značek ASPX, nechte nastavení vlastnosti akce sestavení každého souboru jako vložený prostředek, aby se prostředek mohl kompilovat do satelitního sestavení. Nicméně pokud používáte soubory prostředků pouze k lokalizaci kódu, můžete volitelně změnit akci sestavení na obsah, aby se zabránilo kompilování souboru do hlavního sestavení aplikace.

 Nahraďte všechny řetězce pevně zakódovaných vlastností ve vašich stránkách ASPX a ovládacích prvcích pomocí výrazu v následujícím formátu:

```aspx-csharp
<asp:<class> runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />
```

 Příklad:

```aspx-csharp
<asp:Button ID="btn1" runat="server" onclick="btn1_Click" Text="<%$Resources:Resource1,String7%>"></asp:Button>
```

 Pro ASPX jako text použijte výraz v následujícím formátu:

```aspx-csharp
<asp:literal ID="<ID>" runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />
```

 Příklad:

```aspx-csharp
<asp:literal ID="Literal1" runat="server" Text="<%$Resources:Resource1, String9%>" />
```

 Další informace naleznete v tématu [How to: Localize. aspx Markup](../sharepoint/how-to-localize-aspx-markup.md).

### <a name="localize-code"></a>Lokalizovat kód
 Kromě lokalizace řetězců a [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] značek funkcí je také nutné lokalizovat řetězce zpráv a chybové řetězce, které se zobrazí v kódu řešení. Lokalizované informativní a chybové zprávy jsou obsaženy v satelitních sestaveních. Satelitní sestavení obsahují řetězce, které jsou viditelné uživatelům, například [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] textové a výstupní zprávy, jako jsou výjimky.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] používá standardní .NET Framework hub a paprskový model. Centrum nebo sestavení hlavní aplikace obsahuje výchozí jazykové prostředky. Paprsky nebo satelitní sestavení obsahují prostředky specifické pro jazyk. Další informace najdete v tématu [balení a nasazení prostředků](/previous-versions/dotnet/netframework-4.0/sb6a8618(v=vs.100)). Satelitní sestavení jsou zkompilována ze souborů prostředků (*. resx*). Když do projektu a balíčku řešení přidáte soubory prostředků pro konkrétní jazyk, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zkompiluje soubory prostředků do satelitních sestavení s názvem *{Project Name} .resources.dll*.

 Stejně jako u značek ASPX můžete lokalizovat kód aplikace SharePoint přidáním samostatných prostředků souborových položek projektu do projektu; jeden pro výchozí jazyk a jeden pro každý lokalizovaný jazyk. Jak již bylo zmíněno dříve, pokud již máte soubory prostředků pro lokalizaci značek ASPX, můžete je znovu použít pro lokalizaci kódu. Pokud potřebujete vytvořit soubory prostředků, pojmenujte soubor prostředků výchozího jazyka názvem vaší volby, který je připojený s příponou *. resx* . Pojmenujte lokalizované soubory prostředků se stejným názvem, který je připojený k jazykově specifické jazykové verzi [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] . Nastavte vlastnost Akce sestavení každého souboru prostředků na integrovaný prostředek, aby bylo možné vytvořit satelitní sestavení prostředků.

 Chcete-li vytvořit satelitní sestavení, sestavte projekt a pak přidejte soubory jako další sestavení prostřednictvím karty **Upřesnit** v **Návrháři balíčků**. Při přidávání sestavení předřaďte [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] složku kultury do cesty k umístění, například *DE-de \\ {název položky projektu} .resources.dll*. Balíček tak může obsahovat soubory, které mají stejný název.

 V kódu nahraďte pevně kódované řetězce voláním <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> metody pomocí následující syntaxe:

```aspx-csharp
HttpContext.GetGlobalResourceObject("<Resource File Name>", "<String ID>")
```

 Další informace naleznete v tématu [How to: Localize Code](../sharepoint/how-to-localize-code.md).

#### <a name="web-part-code-localization"></a>Lokalizace kódu webové části
 Webové části obsahují funkci vlastního editoru vlastností, která obsahuje atributy kódu, které používají pevně zakódované řetězce, jako je například WebDisplayName, Category a WebDescription. Chcete-li nahradit hodnoty řetězce pro tyto atributy, vytvořte samostatnou třídu, která je odvozena od třídy atributu. V těchto třídách nastavte vlastnost atributu. Vlastnost atributu závisí na základní třídě. Například vlastnost atributu WebDisplayName je DisplayNameValue a vlastnost atributu WebDescription je DescriptionValue.

 V odvozené třídě odkaz na ID řetězce ze souboru prostředků a objektu ResourceManager pro získání lokalizované hodnoty pro ID řetězce. Vrátí tuto hodnotu k atributu editoru vlastností.

## <a name="see-also"></a>Viz také
- [Postupy: Lokalizace funkce](../sharepoint/how-to-localize-a-feature.md)
- [Postupy: lokalizace značek ASPX](../sharepoint/how-to-localize-aspx-markup.md)
- [Postupy: Lokalizace kódu](../sharepoint/how-to-localize-code.md)
- [Postupy: Přidání souboru prostředků](../sharepoint/how-to-add-a-resource-file.md)
- [Postupy: použití souboru prostředků k určení lokalizovaných názvů, vlastností a oprávnění](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
