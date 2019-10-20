---
title: 'Postupy: Přidání, aktualizace nebo odebrání odkazu na službu WCF Data Service | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- service references [Visual Studio]
- WCF Data Service reference
- WCF data service references
- ADO.NET service references
- ADO.NET Data Service reference
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 89a667e3254be8161d4defb54d524756a5eb02fc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670009"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>Postupy: Přidání, aktualizace nebo odebrání odkazu na službu WCF Data Service
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Odkaz na službu* umožňuje projektu přístup k jednomu nebo více [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)]. Pomocí dialogového okna **Přidat odkaz na službu** můžete vyhledat [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] v aktuálním řešení, místně, v místní síti nebo na internetu.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="adding-a-service-reference"></a>Přidání odkazu na službu

#### <a name="to-add-a-reference-to-an-external-service"></a>Přidání odkazu na externí službu

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na název projektu, do kterého chcete službu přidat, a poté klikněte na položku **Přidat odkaz na službu**.

     Zobrazí se dialogové okno **Přidat odkaz na službu** .

2. Do pole **adresa** zadejte adresu URL služby a potom kliknutím na tlačítko **Přejít** vyhledejte službu. Pokud služba implementuje zabezpečení uživatelského jména a hesla, může se zobrazit výzva k zadání uživatelského jména a hesla.

    > [!NOTE]
    > Měli byste odkazovat jenom na služby z důvěryhodného zdroje. Přidání odkazů z nedůvěryhodného zdroje může ohrozit zabezpečení.

     Můžete také vybrat adresu URL ze seznamu **adres** , ve kterém jsou uloženy předchozí 15 adres URL, na kterých byla nalezena platná metadata služby.

     Při provádění vyhledávání se zobrazí indikátor průběhu. Hledání můžete kdykoli zastavit kliknutím na tlačítko **zastavit**.

3. V seznamu **služby** rozbalte uzel pro službu, kterou chcete použít, a vyberte sadu entit.

4. Do pole **obor názvů** zadejte obor názvů, který chcete použít pro referenci.

5. Kliknutím na tlačítko **OK** přidejte odkaz na projekt.

     Je vygenerován klient služby (proxy) a do souboru App. config je přidána metadata, která popisují službu.

#### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>Přidání odkazu na službu v aktuálním řešení

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na název projektu, do kterého chcete službu přidat, a poté klikněte na položku **Přidat odkaz na službu**.

     Zobrazí se dialogové okno **Přidat odkaz na službu** .

2. Klikněte na tlačítko **zjistit**.

     Do seznamu **služeb** se přidají všechny služby ([!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] i WCF) v aktuálním řešení.

3. V seznamu **služby** rozbalte uzel pro službu, kterou chcete použít, a vyberte sadu entit.

4. Do pole **obor názvů** zadejte obor názvů, který chcete použít pro referenci.

5. Kliknutím na tlačítko **OK** přidejte odkaz na projekt.

     Je vygenerován klient služby (proxy) a do souboru App. config je přidána metadata, která popisují službu.

## <a name="updating-a-service-reference"></a>Aktualizuje se odkaz na službu.
 Model EDM (Entity Data Model) pro [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] se někdy změní. V takovém případě je nutné aktualizovat odkaz na službu.

#### <a name="to-update-a-service-reference"></a>Aktualizace odkazu na službu

- V **Průzkumník řešení**klikněte pravým tlačítkem na odkaz na službu a pak klikněte na **aktualizovat odkaz na službu**.

     Dialogové okno průběh se zobrazí, když se aktualizuje odkaz z jeho původního umístění a klient služby se znovu vygeneruje, aby odrážel všechny změny v metadatech.

## <a name="removing-a-service-reference"></a>Odebrání odkazu na službu
 Pokud se už odkaz na službu nepoužívá, můžete ho odebrat z řešení.

#### <a name="to-remove-a-service-reference"></a>Odebrání odkazu na službu

- V **Průzkumník řešení**klikněte pravým tlačítkem na odkaz na službu a pak klikněte na **Odstranit**.

     Klient služby se odebere z řešení a metadata, která popisují službu, se odeberou ze souboru App. config.

    > [!NOTE]
    > Jakýkoli kód, který odkazuje na odkaz na službu, bude nutné odebrat ručně.

## <a name="see-also"></a>Viz také
 [Služby Windows Communication Foundation a služby WCF Data Services v sadě Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
