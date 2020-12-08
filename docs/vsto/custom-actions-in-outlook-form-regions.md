---
title: Vlastní akce v oblastech formulářů aplikace Outlook
description: Přečtěte si, jak tlačítka pro zobrazení akcí, například odpovědět a odpovědět všem, umožňují uživatelům reagovat na položku systém Microsoft Office Outlook.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], custom actions
- custom actions [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4fe77cddcfe810e73d13de81cc7280969c1d1b1c
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848193"
---
# <a name="custom-actions-in-outlook-form-regions"></a>Vlastní akce v oblastech formulářů aplikace Outlook
  Akce zobrazují tlačítka, která uživatelům umožňují reagovat na položku systém Microsoft Office Outlook. Například pokud chcete reagovat na položku pošty, uživatelé klikněte na tlačítka **Odpovědět**, **Odpovědět všem** nebo **dopředná** akce. Každá z těchto akcí vytvoří novou položku pošty a vyplní pole položky pomocí informací z původní položky.

 Můžete vytvořit vlastní akci, která otevře libovolný druh položky Outlooku. Můžete například přidat vlastní akci, která otevře novou událost nebo položku úkolu. Nastavte vlastnosti vlastní akce nebo použijte vlastní kód k naplnění polí nové položky. Vlastní akce se zobrazí v rozevíracím seznamu **vlastní akce** položky, která je otevřena v okně kontroly aplikace Outlook.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="add-custom-actions-to-a-form-region"></a>Přidání vlastních akcí do oblasti formuláře
 Chcete-li přidat vlastní akci do oblasti formuláře, použijte dialogové okno **vlastní akce** . Můžete otevřít dialogové okno **vlastní akce** výběrem oblasti formuláře v **Průzkumník řešení**, rozbalením uzlu **manifestu** v **okně Vlastnosti**, vybráním vlastnosti **CustomActions** a následným kliknutím na tlačítko se třemi tečkami (![ASP.NET Mobile Designer elipsa](../sharepoint/media/mwellipsis.gif "Elipsa ASP.NET Mobile Designer")).

 K určení *cílového formuláře* můžete použít dialogové okno **vlastní akce** . Cílový formulář je formulář, který se zobrazí, když uživatel spustí vlastní akci.

 Pomocí dialogového okna **vlastní akce** můžete také určit, jak se mají informace z původní položky zobrazovat v cílovém formuláři.

 Následující tabulka popisuje vlastnosti, které jsou k dispozici v dialogovém okně **vlastní akce** .

|Vlastnost|Popis|
|--------------|-----------------|
|**AddressLike**|Určuje způsob, jakým bude směrován cílový formulář.|
|**Text**|Určuje způsob připojení textu původní položky k cílovému formuláři.|
|**Povoleno**|Určuje, zda je vlastní akce povolena. Pokud je tato vlastnost nastavená na **false**, vlastní akce je zakázaná.|
|**Metoda**|Určuje typ odezvy, který je k dispozici při spuštění vlastní akce. Vlastní akce může formulář odeslat, otevřít formulář nebo zobrazit výzvu pro uživatele, zda chce formulář odeslat nebo otevřít.|
|**Název**|Určuje interní název, který lze použít k odkazování na tuto vlastní akci v kódu.|
|**ShowOnRibbon**|Označuje, zda se má na pásu karet původní položky zobrazit vlastní akce.|
|**SubjectPrefix**|Určuje text, který je vložen na začátek řádku předmětu cílového formuláře.|
|**TargetForm**|Určuje název třídy zprávy cílového formuláře. Zadejte například typ **IPM. Úkol** pro otevření formuláře úkolu.|
|**Název**|Určuje popisek tlačítka vlastní akce.|

## <a name="customize-a-custom-action-at-run-time"></a>Přizpůsobení vlastní akce v době běhu
 Chování můžete také přidat do vlastní akce pomocí kódu. Můžete například přidat kód, který přebírá jména příjemců e-mailů a přidává jména jako účastníky nové položky schůzky. Chcete-li to provést, zpracujte událost [CustomAction](/office/vba/api/Outlook.MailItem.CustomAction) [objektu MailItem](/office/vba/api/Outlook.MailItem).

## <a name="see-also"></a>Viz také
- [Vytvoření oblastí formuláře aplikace Outlook](../vsto/creating-outlook-form-regions.md)
- [Návod: návrh oblasti formuláře aplikace Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Přidružení oblasti formuláře k třídě zpráv aplikace Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
