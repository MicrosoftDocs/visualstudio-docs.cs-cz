---
title: Vlastní akce v oblastech formulářů aplikace Outlook
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], custom actions
- custom actions [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4e2ad8e1c3b55d479cb031fe920e3027dbc1788c
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671063"
---
# <a name="custom-actions-in-outlook-form-regions"></a>Vlastní akce v oblastech formulářů aplikace Outlook
  Akce zobrazení tlačítek, které umožní uživatelům na položku Microsoft Office Outlook. Například reakce na položky pošty, uživatelé kliknou **odpověď**, **Odpovědět všem**, nebo **vpřed** akční tlačítka. Všechny tyto akce vytvoří novou položku e-mailu a vyplnit položky pole pomocí informací z původní položky.  
  
 Můžete vytvořit vlastní akci, která otevře jakýkoli druh položky aplikace Outlook. Například můžete přidat vlastní akci, která se otevře nová položka událost nebo task. Nastavit vlastnosti vlastní akce nebo použít vlastní kód k vyplnění polí nové položky. Vlastní akce se zobrazí v **vlastní akce** rozevíracího seznamu položky, který je otevřen v okně Inspektor aplikace Outlook.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="add-custom-actions-to-a-form-region"></a>Přidat vlastní akce pro oblasti formuláře  
 Chcete-li přidat vlastní akci pro oblasti formuláře, použijte **vlastní akce** dialogové okno. Můžete otevřít **vlastní akce** dialogové okno v **Průzkumníku řešení** tak, že rozbalíte **Manifest** uzlu, vyberte **CustomActions**vlastnost a potom kliknutím na tlačítko se třemi tečkami (![ASP.NET Mobilní návrháře Elipsa](../sharepoint/media/mwellipsis.gif "ASP.NET – Návrhář mobilních řešení Elipsa")).  
  
 Můžete použít **vlastní akce** dialogové okno k zadání *cílit na formulář*. Formulář Cíl je formulář, který se zobrazí, když uživatel provede vlastní akci.  
  
 Můžete také použít **vlastní akce** dialogové okno k určení, jak chcete informace z původní položky se zobrazí ve formuláři cíl.  
  
 Následující tabulka popisuje vlastnosti, které jsou k dispozici v **vlastní akce** dialogové okno.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|**AddressLike**|Určuje, jak bude řešit cílového formuláře.|  
|**Text**|Určuje, jak tělo původní položky se připojí k cílové formuláře.|  
|**Povoleno**|Určuje, zda je povoleno vlastní akce. Pokud je tato vlastnost nastavená na **false**, vlastní akce je zakázaná.|  
|**– Metoda**|Určuje typ odpovědi, které jsou k dispozici při provedení vlastní akce. Vlastní akce můžete odeslat formulář, otevřete formulář nebo výzva, jestli chce odeslat nebo otevřete formulář.|  
|**Jméno**|Určuje interní název, který vám pomůže odkazovat na tato vlastní akce v kódu.|  
|**ShowOnRibbon**|Určuje, jestli se má zobrazit na pásu karet původní položka vlastní akce.|  
|**SubjectPrefix**|Určuje text, který bude vložena na začátek řádku předmětu cílového formuláře.|  
|**TargetForm**|Určuje název třídy zpráv cílového formuláře. Zadejte například **IPM. Úloha** otevřete formulář úloh.|  
|**Název**|Určuje popisek tlačítka pro vlastní akci.|  
  
## <a name="customize-a-custom-action-at-runtime"></a>Přizpůsobit vlastní akci za běhu  
 Chování můžete také přidat vlastní akci pomocí kódu. Můžete například přidat kód, který přebírá jména příjemců e-mailu a přidá tyto názvy jako účastníků v nové položky události na zařízení. K tomuto účelu zpracování [CustomAction](/office/vba/api/Outlook.MailItem.CustomAction) událost [MailItem objekt](/office/vba/api/Outlook.MailItem).  
  
## <a name="see-also"></a>Viz také:  
 [Vytváření oblastí formulářů aplikace Outlook](../vsto/creating-outlook-form-regions.md)   
 [Návod: Návrh oblasti formuláře Outlooku](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Přidružení oblasti formuláře k třídě zpráv aplikace Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)  
  
  