---
title: 'Návod: Přidání přijímačů událostí funkce | Microsoft Docs'
description: V tomto návodu přidejte přijímače událostí funkcí, což jsou metody, které se spustí, když je nainstalovaná, aktivovaná, deaktivovaná nebo odebraná funkce SharePointu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, advanced packaging tools
- SharePoint development in Visual Studio, event receivers
- SharePoint development in Visual Studio, feature event receivers
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 98b85222fca4da6dfca653ad74e1315801798d83
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915593"
---
# <a name="walkthrough-add-feature-event-receivers"></a>Návod: Přidání přijímačů událostí funkce
Přijímače událostí funkcí jsou metody, které se spustí, když se v SharePointu vyskytne jedna z následujících událostí souvisejících s funkcemi:

- Je nainstalována funkce.

- Aktivuje se funkce.

- Aktivuje se funkce.

- Funkce je odebrána.

Tento návod ukazuje, jak přidat přijímač událostí do funkce v projektu služby SharePoint. Ukazuje následující úlohy:

- Vytvoření prázdného projektu pomocí přijímače událostí funkce.

- Zpracovává se metoda **FeatureDeactivating** .

- Pomocí modelu objektu projektu služby SharePoint můžete přidat oznámení do seznamu oznámení.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Předpoklady
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- Podporované edice Microsoft Windows a SharePointu.

- Visual Studio

## <a name="create-a-feature-event-receiver-project"></a>Vytvořit projekt přijímače událostí funkcí
 Nejprve vytvořte projekt, který bude obsahovat přijímač událostí funkce.

#### <a name="to-create-a-project-with-a-feature-event-receiver"></a>Vytvoření projektu s funkcí přijímače událostí

1. Na panelu nabídek vyberte možnost **soubor**  >  **Nový**  >  **projekt** . zobrazí se dialogové okno **Nový projekt** .

2. Rozbalte uzel **služby SharePoint** v rámci **jazyka Visual C#** nebo **Visual Basic** a pak vyberte uzel **2010** .

3. V podokně **šablony** vyberte šablonu **projektu SharePoint 2010** .

     Tento typ projektu použijete pro přijímače událostí funkcí, protože nemají žádnou šablonu projektu.

4. Do pole **název** zadejte **FeatureEvtTest** a potom kliknutím na tlačítko **OK** zobrazte **Průvodce přizpůsobením SharePointu**.

5. Na stránce **Zadejte lokalitu a úroveň zabezpečení pro ladění** zadejte adresu URL serveru SharePoint Server, na který chcete přidat novou položku vlastního pole, nebo použijte výchozí umístění (http:// \<*system name*> /).

6. V části **co je úroveň důvěryhodnosti pro toto řešení služby SharePoint?** vyberte možnost **nasadit jako řešení farmy** .

     Další informace o řešeních v izolovaném prostoru a řešeních farmy najdete v tématu [požadavky na řešení v izolovaném prostoru](../sharepoint/sandboxed-solution-considerations.md).

7. Klikněte na tlačítko **Dokončit** a pak si všimněte, že se pod uzlem **funkce** zobrazí funkce s názvem Feature1.

## <a name="add-an-event-receiver-to-the-feature"></a>Přidání přijímače událostí do funkce
 Dále přidejte do funkce přijímač událostí a přidejte kód, který se spustí při deaktivaci funkce.

#### <a name="to-add-an-event-receiver-to-the-feature"></a>Přidání přijímače událostí do funkce

1. Otevřete místní nabídku uzlu funkce a pak zvolte možnost **Přidat funkci** a vytvořte funkci.

2. V uzlu **funkce** otevřete místní nabídku pro **Feature1** a pak zvolte **Přidat přijímač událostí** a přidejte do této funkce přijímač událostí.

     Tím se do Feature1 přidá soubor kódu. V tomto případě se jmenuje buď *Feature1.EventReceiver.cs* nebo *Feature1. EventReceiver. vb*, v závislosti na vývojovém jazyku vašeho projektu.

3. Pokud je projekt napsán v [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] , přidejte do horní části přijímače událostí následující kód, pokud tam ještě není:

     [!code-csharp[SP_FeatureEvt#1](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#1)]

4. Třída přijímač událostí obsahuje několik metod s komentářem, které fungují jako události. Metodu **FeatureDeactivating** nahraďte následujícím:

     [!code-vb[SP_FeatureEvt#2](../sharepoint/codesnippet/VisualBasic/featureevt2vb/features/feature1/feature1.eventreceiver.vb#2)]
     [!code-csharp[SP_FeatureEvt#2](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#2)]

## <a name="test-the-feature-event-receiver"></a>Test přijímače událostí funkcí
 Dále dezaktivujte funkci pro otestování, zda metoda **FeatureDeactivating** vypisuje oznámení do seznamu oznámení služby SharePoint.

#### <a name="to-test-the-feature-event-receiver"></a>Otestování přijímače událostí funkcí

1. Nastavte hodnotu vlastnosti **Konfigurace aktivního nasazení** projektu na **bez aktivace**.

     Nastavením této vlastnosti zabráníte funkci v aktivaci služby SharePoint a budete moci ladit přijímače událostí funkcí. Další informace najdete v tématu [ladění řešení služby SharePoint](../sharepoint/debugging-sharepoint-solutions.md).

2. Kliknutím na klávesu **F5** spusťte projekt a nasaďte ho na SharePoint.

3. V horní části webové stránky služby SharePoint otevřete nabídku **Akce webu** a zvolte možnost **Nastavení webu**.

4. V části **Akce webu** na stránce **nastavení lokality** vyberte odkaz **Spravovat funkce webu** .

5. Na stránce **funkce** klikněte na tlačítko **aktivovat** vedle funkce **FeatureEvtTest Feature1** .

6. Na stránce **funkce** klikněte na tlačítko **deaktivovat** vedle funkce **FeatureEvtTest Feature1** a pak klikněte na odkaz **deaktivovat tuto funkci** pro deaktivaci této funkce.

7. Klikněte na tlačítko **Domů** .

     Všimněte si, že se oznámení zobrazí v seznamu **oznámení** po deaktivaci této funkce.

## <a name="see-also"></a>Viz také

- [Postupy: vytvoření přijímače událostí](../sharepoint/how-to-create-an-event-receiver.md)
- [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)