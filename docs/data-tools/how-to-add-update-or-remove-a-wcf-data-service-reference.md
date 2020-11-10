---
title: Přidání, aktualizace nebo odebrání odkazu na službu WCF Data Service
description: Přečtěte si, jak přidat, aktualizovat nebo odebrat odkaz na datovou službu Windows Communication Foundation (WCF).
ms.date: 11/04/2016
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- service references [Visual Studio]
- WCF Data Service reference
- WCF data service references
- ADO.NET service references
- ADO.NET Data Service reference
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6e6c289038c3f8cb9d1586ae4a1f7a84b563239f
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436430"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>Postupy: Přidání, aktualizace nebo odebrání odkazu na službu WCF Data Service

::: moniker range="vs-2017"
*Odkaz na službu* umožňuje projektu přístup k jednomu nebo více [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] . Pomocí dialogového okna **Přidat odkaz na službu** můžete vyhledat [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] v aktuálním řešení, místně, v místní síti nebo na internetu.
::: moniker-end
::: moniker range=">=vs-2019"
Uzel **připojené služby** v **Průzkumník řešení** můžete použít pro přístup k **Microsoft WCF Web Service reference Provider** , který umožňuje spravovat odkazy na datové služby Windows Communication Foundation (WCF).
::: moniker-end

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-a-wcf-service-reference"></a>Přidat odkaz na službu WCF

### <a name="to-add-a-reference-to-an-external-service"></a>Přidání odkazu na externí službu

::: moniker range="vs-2017"

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na název projektu, do kterého chcete přidat službu, a pak klikněte na **Přidat odkaz na službu**.

   Zobrazí se dialogové okno **Přidat odkaz na službu** .

1. Do pole **adresa** zadejte adresu URL služby a potom kliknutím na tlačítko **Přejít** vyhledejte službu. Pokud služba implementuje zabezpečení uživatelského jména a hesla, může se zobrazit výzva k zadání uživatelského jména a hesla.

    > [!NOTE]
    > Měli byste odkazovat jenom na služby z důvěryhodného zdroje. Přidání odkazů z nedůvěryhodného zdroje může ohrozit zabezpečení.

     Můžete také vybrat adresu URL ze seznamu **adres** , ve kterém jsou uloženy předchozí 15 adres URL, na kterých byla nalezena platná metadata služby.

     Po provedení hledání se zobrazí indikátor průběhu. Hledání můžete kdykoli zastavit kliknutím na tlačítko **zastavit**.

1. V seznamu **služby** rozbalte uzel pro službu, kterou chcete použít, a vyberte sadu entit.

1. Do pole **obor názvů** zadejte obor názvů, který chcete použít pro referenci.

1. Kliknutím na tlačítko **OK** přidejte odkaz na projekt.

     Dojde k vygenerování klienta služby (proxy) a do souboru *app.config* přidat metadata, která popisují službu.
::: moniker-end
::: moniker range=">=vs-2019"
1. V **Průzkumník řešení** dvakrát klikněte nebo klepněte na uzel **připojené služby** .

   Otevře se karta **Konfigurovat služby** .

1. Vyberte **Microsoft WCF Web Service reference Provider**.

   Zobrazí se dialogové okno **Konfigurovat odkaz na webovou službu WCF** .

   ![Snímek obrazovky dialogového okna poskytovatele webové služby WCF](media/vs-2019/configure-wcf-web-service-reference-dialog.png)


1. Do pole **identifikátor URI** zadejte adresu URL služby a potom kliknutím na tlačítko **Přejít** vyhledejte službu. Pokud služba implementuje zabezpečení uživatelského jména a hesla, může se zobrazit výzva k zadání uživatelského jména a hesla.

    > [!NOTE]
    > Měli byste odkazovat jenom na služby z důvěryhodného zdroje. Přidání odkazů z nedůvěryhodného zdroje může ohrozit zabezpečení.

     Můžete taky vybrat adresu URL ze seznamu **identifikátorů URI** , ve které se uloží předchozí 15 adres URL, na kterých se našla platná metadata služby.

     Po provedení hledání se zobrazí indikátor průběhu. Hledání můžete kdykoli zastavit kliknutím na tlačítko **zastavit**.

1. V seznamu **služby** rozbalte uzel pro službu, kterou chcete použít, a vyberte sadu entit.

1. Do pole **obor názvů** zadejte obor názvů, který chcete použít pro referenci.

1. Kliknutím na tlačítko **Dokončit** přidejte odkaz na projekt.

     Dojde k vygenerování klienta služby (proxy) a do souboru *app.config* přidat metadata, která popisují službu.

::: moniker-end

### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>Přidání odkazu na službu v aktuálním řešení

::: moniker range="vs-2017"

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na název projektu, do kterého chcete přidat službu, a pak klikněte na **Přidat odkaz na službu**.

    Zobrazí se dialogové okno **Přidat odkaz na službu** .

1. Klikněte na tlačítko **Zjistit**.

    Do [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] seznamu **služeb** se přidají všechny služby (a služby WCF) v aktuálním řešení.

1. V seznamu **služby** rozbalte uzel pro službu, kterou chcete použít, a vyberte sadu entit.

1. Do pole **obor názvů** zadejte obor názvů, který chcete použít pro referenci.

1. Kliknutím na tlačítko **OK** přidejte odkaz na projekt.

    Klient služby (proxy) vygeneruje a metadata, která popisují službu, se přidají do souboru *app.config* .
::: moniker-end
::: moniker range=">=vs-2019"
1. V **Průzkumník řešení** dvakrát klikněte nebo klepněte na uzel **připojené služby** . 

   Otevře se karta **Konfigurovat služby** .

1. Vyberte **Microsoft WCF Web Service reference Provider**.

   Zobrazí se dialogové okno **Konfigurovat odkaz na webovou službu WCF** .

1. Klikněte na tlačítko **Zjistit**.

    Do [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] seznamu **služeb** se přidají všechny služby (a služby WCF) v aktuálním řešení.

1. V seznamu **služby** rozbalte uzel pro službu, kterou chcete použít, a vyberte sadu entit.

1. Do pole **obor názvů** zadejte obor názvů, který chcete použít pro referenci.

1. Kliknutím na tlačítko **Dokončit** přidejte odkaz na projekt.

    Klient služby (proxy) vygeneruje a metadata, která popisují službu, se přidají do souboru *app.config* .

::: moniker-end

## <a name="update-a-service-reference"></a>Aktualizovat odkaz na službu

Model EDM (Entity Data Model) se [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] někdy změní. Pokud k tomu dojde, musíte aktualizovat odkaz na službu.

### <a name="to-update-a-service-reference"></a>Aktualizace odkazu na službu

- V **Průzkumník řešení** klikněte pravým tlačítkem na odkaz na službu a pak klikněte na **aktualizovat odkaz na službu**.

     Dialogové okno průběh se zobrazí, když je odkaz aktualizován z jeho původního umístění a klient služby se znovu vygeneruje, aby odrážel všechny změny v metadatech.

## <a name="remove-a-service-reference"></a>Odebrat odkaz na službu

Pokud se už odkaz na službu nepoužívá, můžete ho odebrat z řešení.

### <a name="to-remove-a-service-reference"></a>Odebrání odkazu na službu

- V **Průzkumník řešení** klikněte pravým tlačítkem na odkaz na službu a pak klikněte na **Odstranit**.

     Klient služby se odebere z řešení a metadata, která popisují službu, se odeberou z *app.config* souboru.

    > [!NOTE]
    > Jakýkoli kód, který odkazuje na odkaz na službu, je nutné odebrat ručně.

## <a name="see-also"></a>Viz také

- [Služby Windows Communication Foundation Services a WCF Data Services v aplikaci Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
