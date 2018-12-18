---
title: 'Postupy: Přidání, aktualizace nebo odebrání odkazu na službu WCF Data | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- service references [Visual Studio]
- WCF Data Service reference
- WCF data service references
- ADO.NET service references
- ADO.NET Data Service reference
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b14a83b195809dff89fa89bb6fcf91050e2f8a0c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49192254"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>Postupy: Přidání, aktualizace nebo odebrání odkazu na službu WCF Data Service
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
A *odkaz na službu* umožňuje přístup k jedné nebo více projektu [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)]. Použití **přidat odkaz na službu** dialogové okno pro hledání [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] v aktuálním řešení místně, v místní síti nebo na Internetu.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="adding-a-service-reference"></a>Přidání odkazu na službu  
  
#### <a name="to-add-a-reference-to-an-external-service"></a>Chcete-li přidat odkaz na externí služby  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na název projektu, který chcete přidat službu a pak klikněte na tlačítko **přidat odkaz na službu**.  
  
     **Přidat odkaz na službu** zobrazí se dialogové okno.  
  
2.  V **adresu** pole, zadejte adresu URL pro službu a pak klikněte na tlačítko **Přejít** k vyhledání služby. Pokud služba implementuje uživatelské jméno a heslo zabezpečení, vám může zobrazit výzva k zadání uživatelského jména a hesla.  
  
    > [!NOTE]
    >  Služby by měly odkazovat pouze z důvěryhodného zdroje. Přidávání odkazů z nedůvěryhodných zdrojů může ohrozit zabezpečení.  
  
     Můžete také vybrat adresu URL **adresu** seznam, který ukládá předchozí 15 adresy URL, na kterých byla nalezena platná metadata služby.  
  
     Při hledání se zobrazí indikátor průběhu. Hledání v každém okamžiku může ukončit kliknutím na **Zastavit**.  
  
3.  V **služby** seznamu, rozbalte uzel pro službu, kterou chcete použít a vyberte sadu entit.  
  
4.  V **Namespace** , zadejte obor názvů, který chcete použít pro odkaz na pole.  
  
5.  Klikněte na tlačítko **OK** přidáte odkaz na projekt.  
  
     Klient služby (proxy) je generován a metadata, která popisuje službu se přidá do souboru app.config.  
  
#### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>Chcete-li přidat odkaz na službu v aktuálním řešení  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na název projektu, který chcete přidat službu a pak klikněte na tlačítko **přidat odkaz na službu**.  
  
     **Přidat odkaz na službu** zobrazí se dialogové okno.  
  
2.  Klikněte na tlačítko **zjistit**.  
  
     Všechny služby (obojí [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] a služby WCF) v aktuálním řešení se přidají do **služby** seznamu.  
  
3.  V **služby** seznamu, rozbalte uzel pro službu, kterou chcete použít a vyberte sadu entit.  
  
4.  V **Namespace** , zadejte obor názvů, který chcete použít pro odkaz na pole.  
  
5.  Klikněte na tlačítko **OK** přidáte odkaz na projekt.  
  
     Klient služby (proxy) je generován a metadata, která popisuje službu se přidá do souboru app.config.  
  
## <a name="updating-a-service-reference"></a>Aktualizuje se odkaz na službu  
 Datový Model Entity pro [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] někdy změní. Pokud k tomu dojde, je třeba aktualizovat odkaz na službu.  
  
#### <a name="to-update-a-service-reference"></a>Chcete-li aktualizovat odkaz na službu  
  
-   V **Průzkumníka řešení**, klikněte pravým tlačítkem na odkaz na službu a pak klikněte na tlačítko **aktualizovat odkaz na službu**.  
  
     Odkaz je aktualizována z původního umístění a klient služby je vygenerován tak, aby odrážela všechny změny v metadatech, zobrazí se dialogové okno průběhu.  
  
## <a name="removing-a-service-reference"></a>Odebírá se odkaz na službu  
 Pokud je již nejsou déle používány odkaz na službu, můžete ho odebrat z vašeho řešení.  
  
#### <a name="to-remove-a-service-reference"></a>Chcete-li odebrat odkaz na službu  
  
-   V **Průzkumníka řešení**, klikněte pravým tlačítkem na odkaz na službu a pak klikněte na tlačítko **odstranit**.  
  
     Klient služby bude odebrán z řešení a metadat, který popisuje službu se odebere ze souboru app.config.  
  
    > [!NOTE]
    >  Veškerý kód, který odkazuje na odkaz na službu muset odebrat ručně.  
  
## <a name="see-also"></a>Viz také  
 [Služby Windows Communication Foundation a služby WCF Data Services v sadě Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

