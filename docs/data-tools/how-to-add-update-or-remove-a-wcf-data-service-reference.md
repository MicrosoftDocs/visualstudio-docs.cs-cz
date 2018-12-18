---
title: 'Postupy: Přidání, aktualizace nebo odebrání odkazu na službu WCF Data Service'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- service references [Visual Studio]
- WCF Data Service reference
- WCF data service references
- ADO.NET service references
- ADO.NET Data Service reference
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 9099c1ee0b1ed3af108c11792f7629453dfbf7c6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49819040"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>Postupy: Přidání, aktualizace nebo odebrání odkazu na datovou službu WCF
A *odkaz na službu* umožňuje přístup k jedné nebo více projektu [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]. Použití **přidat odkaz na službu** dialogové okno pro hledání [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] v aktuálním řešení místně, v místní síti nebo na Internetu.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-a-service-reference"></a>Přidání odkazu na službu

### <a name="to-add-a-reference-to-an-external-service"></a>Chcete-li přidat odkaz na externí služby

1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na název projektu, ke kterému chcete přidat službu a pak klikněte na tlačítko **přidat odkaz na službu**.

     **Přidat odkaz na službu** zobrazí se dialogové okno.

2.  V **adresu** pole, zadejte adresu URL pro službu a pak klikněte na tlačítko **Přejít** k vyhledání služby. Pokud služba implementuje uživatelské jméno a heslo zabezpečení, vám může zobrazit výzva k zadání uživatelského jména a hesla.

    > [!NOTE]
    >  Služby by měly odkazovat pouze z důvěryhodného zdroje. Přidávání odkazů z nedůvěryhodných zdrojů může ohrozit zabezpečení.

     Můžete také vybrat adresu URL **adresu** seznam, který ukládá předchozí 15 adresy URL, na kterých byla nalezena platná metadata služby.

     Při hledání se zobrazí indikátor průběhu. Hledání v každém okamžiku může ukončit kliknutím na **Zastavit**.

3.  V **služby** seznamu, rozbalte uzel pro službu, kterou chcete použít a vyberte sadu entit.

4.  V **Namespace** , zadejte obor názvů, který chcete použít pro odkaz na pole.

5.  Klikněte na tlačítko **OK** přidáte odkaz na projekt.

     Klient služby (proxy) se vygeneruje, a do se přidají metadata, který popisuje službu *app.config* souboru.

### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>Chcete-li přidat odkaz na službu v aktuálním řešení

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na název projektu, ke kterému chcete přidat službu a pak klikněte na tlačítko **přidat odkaz na službu**.

    **Přidat odkaz na službu** zobrazí se dialogové okno.

2. Klikněte na tlačítko **zjistit**.

    Všechny služby (obojí [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] a služby WCF) v aktuálním řešení se přidají do **služby** seznamu.

3. V **služby** seznamu, rozbalte uzel pro službu, kterou chcete použít a vyberte sadu entit.

4. V **Namespace** , zadejte obor názvů, který chcete použít pro odkaz na pole.

5. Klikněte na tlačítko **OK** přidáte odkaz na projekt.

    Generuje služba klienta (proxy) a do se přidají metadata, který popisuje službu *app.config* souboru.

## <a name="update-a-service-reference"></a>Aktualizovat odkaz na službu
 Datový Model Entity pro [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] někdy dochází ke změnám. Pokud k tomu dojde, je nutné aktualizovat odkaz na službu.

### <a name="to-update-a-service-reference"></a>Chcete-li aktualizovat odkaz na službu

-   V **Průzkumníka řešení**, klikněte pravým tlačítkem na odkaz na službu a pak klikněte na tlačítko **aktualizovat odkaz na službu**.

     Při odkazu je aktualizována z původního umístění a klienta služby se znova vygeneroval tak, aby odrážela všechny změny v metadatech se zobrazí dialogové okno průběhu.

## <a name="remove-a-service-reference"></a>Odebrat odkaz na službu
 Pokud je již nejsou déle používány odkaz na službu, můžete ho odebrat z vašeho řešení.

### <a name="to-remove-a-service-reference"></a>Chcete-li odebrat odkaz na službu

-   V **Průzkumníka řešení**, klikněte pravým tlačítkem na odkaz na službu a pak klikněte na tlačítko **odstranit**.

     Klient služby bude odebrán z řešení a metadat, který popisuje službu se odebere z *app.config* souboru.

    > [!NOTE]
    >  Veškerý kód, který odkazuje na odkaz na službu musí ručně odebrat.

## <a name="see-also"></a>Viz také:

- [Služby Windows Communication Foundation a WCF data services v sadě Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)