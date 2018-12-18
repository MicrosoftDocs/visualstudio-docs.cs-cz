---
title: 'Postupy: Připojování k datům ve službě'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], connecting to web services
- data sources, creating from web services
- data [Visual Studio], reading from web services
- reading data, from web services
- web services, reading data
- web services, as data sources
- web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: f8f7371418df19ec8452334641c7c9414328e557
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305010"
---
# <a name="how-to-connect-to-data-in-a-service"></a>Postupy: připojení k datům ve službě

Připojení vaší aplikace s daty vrácenými ze služby spuštěním [Průvodce konfigurací zdroje dat](../data-tools/media/data-source-configuration-wizard.png) a vyberete **služby** na **zvolte typ zdroje dat**stránky.

Po dokončení průvodce se odkaz na službu se přidá do vašeho projektu a je okamžitě k dispozici v [okna zdroje dat](add-new-data-sources.md#data-sources-window).

> [!NOTE]
> Položky, které se zobrazují v **zdroje dat** okna jsou závislé na informace, které služba vrací. Některé služby nemusí poskytnout dostatek informací, **Průvodce konfigurací zdroje dat** vytvořil objekty. Například pokud služba vrátí netypovou datovou sadu, žádné položky, které se zobrazí v **zdroje dat** po dokončení průvodce. Je to proto netypové datové sady neposkytují schéma, proto Průvodce nemá dostatek informací pro vytvoření zdroje dat.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-connect-your-application-to-a-service"></a>Pro připojení aplikace ke službě

1.  Na **Data** nabídky, klikněte na tlačítko **přidat nový zdroj dat**.

2.  Vyberte **služby** na **zvolte typ zdroje dat** stránce a potom klikněte na tlačítko **Další**.

3.  Zadejte adresu služby, kterou chcete použít, nebo klikněte na tlačítko **Discover** vyhledejte služby v aktuálním řešení a potom klikněte na **Přejít**.

4.  Volitelně můžete zadat nový **Namespace** místo výchozí hodnotu.

    > [!NOTE]
    > Klikněte na tlačítko **Upřesnit** otevřít [dialogové okno nastavit odkaz na službu](../data-tools/configure-service-reference-dialog-box.md).

5.  Klikněte na tlačítko **OK** přidáte odkaz na službu do projektu.

6.  Klikněte na tlačítko **Dokončit**.

     Zdroj dat je přidaný do **zdroje dat** okna.

## <a name="next-steps"></a>Další kroky

Chcete-li přidat funkce do vaší aplikace, vyberte položku v **zdroje dat** okno a přetáhněte jej na formulář pro vytvoření vazby ovládacích prvků. Další informace najdete v tématu [vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="see-also"></a>Viz také:

- [Vytvoření vazby ovládacích prvků WPF k datové službě WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)
- [Služby Windows Communication Foundation a WCF data services v sadě Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)