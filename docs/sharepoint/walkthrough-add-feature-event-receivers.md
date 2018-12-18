---
title: 'Návod: Přidání přijímačů událostí funkce | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, advanced packaging tools
- SharePoint development in Visual Studio, event receivers
- SharePoint development in Visual Studio, feature event receivers
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4ab2eded41d9416f03592c9346a379f8a276366a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49948761"
---
# <a name="walkthrough-add-feature-event-receivers"></a>Návod: Přidání přijímačů událostí funkce
  Přijímače událostí funkcí jsou metody, které jsou spuštěny při jedné z následujících událostí související s funkcí ve službě SharePoint:

- Instalace součásti.

- Se funkce aktivuje.

- Funkce je deaktivováno.

- Funkce se odebere.

  Tento návod ukazuje, jak přidat přijímače událostí funkcí v projektu služby SharePoint. To demonstruje následující úkoly:

- Vytvoření prázdného projektu pomocí příjemce událostí funkce.

- Zpracování **FeatureDeactivating** metody.

- Přidání oznámení do seznamu oznámení pomocí objektového modelu projektu SharePoint.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu budete potřebovat následující komponenty:

-   Podporované vydání systému Microsoft Windows a SharePoint.

-   Visual Studio.

## <a name="create-a-feature-event-receiver-project"></a>Vytvoření projektu příjemce událostí funkce
 Nejprve vytvořte projekt tak, aby obsahovala příjemce událostí funkce.

#### <a name="to-create-a-project-with-a-feature-event-receiver"></a>Vytvoření projektu s příjemce událostí funkce

1.  V panelu nabídky zvolte **souboru** > **nový** > **projektu** zobrazíte **nový projekt** dialogové okno.

2.  Rozbalte **SharePoint** uzlu buď **Visual C#** nebo **jazyka Visual Basic**a klikněte na tlačítko **2010** uzlu.

3.  V **šablony** podokně, vyberte **projektu služby SharePoint 2010** šablony.

     Tento typ projektu pro přijímačů událostí funkce použít, protože nemají žádné šablony projektu.

4.  V **název** zadejte **FeatureEvtTest**a klikněte na tlačítko **OK** tlačítka pro zobrazení **Průvodce přizpůsobením SharePoint**.

5.  Na **zadejte web a úroveň zabezpečení pro ladění** stránky, zadejte adresu URL webu služby SharePoint server, ke kterému chcete přidat novou položku vlastní pole nebo použijte výchozí umístění (http://\<*systému název*> /).

6.  V **co je úroveň důvěryhodnosti pro toto řešení SharePoint?** zvolte **nasadit jako řešení farmy** přepínač.

     Další informace o řešení v izolovaném prostoru a řešení farmy najdete v tématu [aspekty řešení v izolovaném prostoru](../sharepoint/sandboxed-solution-considerations.md).

7.  Zvolte **Dokončit** tlačítko a Všimněte si, že funkce, která má název Feature1 je zobrazen **funkce** uzlu.

## <a name="add-an-event-receiver-to-the-feature"></a>Přidat přijímače událostí pro funkci
 V dalším kroku přidat přijímače událostí pro funkci a přidejte kód, který se spustí při deaktivaci funkce.

#### <a name="to-add-an-event-receiver-to-the-feature"></a>Chcete-li přidat přijímače událostí pro funkci

1.  Otevřete místní nabídku pro uzel funkce a klikněte na tlačítko **přidat funkci** , aby vytvořil funkci.

2.  V části **funkce** uzel, otevřete místní nabídku pro **Feature1**a klikněte na tlačítko **přidat příjemce událostí** přidat přijímače událostí pro funkci.

     Tím se přidá soubor kódu v rámci Feature1. V takovém případě je buď název *Feature1.EventReceiver.cs* nebo *Feature1.EventReceiver.vb*, v závislosti na vývojovém jazyce vašeho projektu.

3.  Pokud váš projekt je napsán [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)], přidejte následující kód v horní části příjemce událostí, pokud ještě není:

     [!code-csharp[SP_FeatureEvt#1](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#1)]

4.  Přijímače událostí obsahuje několik metod komentovaná, které se chovají jako události. Nahradit **FeatureDeactivating** metoda následujícím kódem:

     [!code-vb[SP_FeatureEvt#2](../sharepoint/codesnippet/VisualBasic/featureevt2vb/features/feature1/feature1.eventreceiver.vb#2)]
     [!code-csharp[SP_FeatureEvt#2](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#2)]

## <a name="test-the-feature-event-receiver"></a>Test příjemce událostí funkce
 V dalším kroku deaktivovat funkci otestovat, jestli **FeatureDeactivating** metoda výstup hlášení do seznamu Sharepointu oznámení.

#### <a name="to-test-the-feature-event-receiver"></a>K otestování příjemce událostí funkce

1.  Nastavte hodnotu vlastnosti projektu **aktivní konfiguraci nasazení** vlastnost **bez aktivace**.

     Nastavení této vlastnosti funkci brání aktivaci ve službě SharePoint a umožňuje ladění přijímačů událostí funkce. Další informace najdete v tématu [řešení ladění služby SharePoint](../sharepoint/debugging-sharepoint-solutions.md).

2.  Zvolte **F5** klávesy spusťte projekt a nasaďte ji do služby SharePoint.

3.  V horní části stránky na webu služby SharePoint, otevřete **Akce webu** nabídky a klikněte na tlačítko **nastavení webu**.

4.  V části **Akce webu** část **nastavení webu** zvolte **spravovat funkce webu** odkaz.

5.  Na **funkce** zvolte **aktivovat** vedle **FeatureEvtTest Feature1** funkce.

6.  Na **funkce** zvolte **deaktivovat** vedle **FeatureEvtTest Feature1** funkce a klikněte na tlačítko **deaktivovat tuto funkci**  potvrzovacího odkazu deaktivace funkce.

7.  Zvolte **Domů** tlačítko.

     Všimněte si, že se zobrazí v oznámení **oznámení** seznamu po deaktivaci funkce.

## <a name="see-also"></a>Viz také:

- [Postupy: vytvoření přijímače událostí](../sharepoint/how-to-create-an-event-receiver.md)
- [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)