---
title: Konfigurace projektu cloudové služby Azure
description: Zjistěte, jak nakonfigurovat projekt cloudové služby Azure v sadě Visual Studio, v závislosti na vašich požadavcích na tento projekt.
author: ghogen
manager: jillfra
assetId: 609d6965-05cc-47b1-82dc-c76a92d4f295
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/06/2017
ms.author: ghogen
ms.openlocfilehash: 609830b5182ef726a6d1933acecb1ddcbf4e25ef
ms.sourcegitcommit: 59a8732dc563242590f7c6ccf4ced6c6d195533c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81489698"
---
# <a name="configure-an-azure-cloud-service-project-with-visual-studio"></a>Konfigurace projektu cloudové služby Azure v sadě Visual Studio
Projekt cloudové služby Azure můžete nakonfigurovat v závislosti na vašich požadavcích na tento projekt. Můžete nastavit vlastnosti projektu pro následující kategorie:

- **Publikování cloudové služby do Azure** – můžete nastavit vlastnost a ujistěte se, že existující cloudová služba nasazená do Azure není omylem odstraněna.
- **Spuštění nebo ladění cloudové služby v místním počítači** – můžete vybrat konfiguraci služby, která se má použít, a určit, jestli chcete spustit emulátor úložiště Azure.
- **Ověřte balíček cloudové služby při jeho vytvoření** – můžete se rozhodnout považovat všechna upozornění za chyby, abyste zajistili, že balíček cloudových služeb nasadí bez problémů.

## <a name="steps-to-configure-an-azure-cloud-service-project"></a>Postup konfigurace projektu cloudové služby Azure
1. Otevření nebo vytvoření projektu cloudové služby v sadě Visual Studio

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt a v kontextové nabídce vyberte **příkaz Vlastnosti**.

1. Na stránce vlastností projektu vyberte kartu **Vývoj.**

    ![Nabídka vlastností projektu](./media/vs-azure-tools-configuring-an-azure-project/solution-explorer-project-properties-menu.png)

1. Před **odstraněním existujícího nasazení** na **hodnotu True**nastavte výzvu. Toto nastavení pomáhá zajistit, že omylem neodstraníte stávající nasazení v Azure.

1. Vyberte požadovanou **konfiguraci služby** a označte, kterou konfiguraci služby chcete použít při místním spuštění nebo ladění cloudové služby. Další informace o tom, jak upravit konfiguraci služby pro roli, najdete v [tématu Jak nakonfigurovat role pro cloudovou službu Azure pomocí sady Visual Studio](./vs-azure-tools-configure-roles-for-cloud-service.md).

1. Nastavte **spustit emulátor úložiště Azure** na **True,** abyste spustili emulátor úložiště Azure, když spustíte nebo ladíte cloudovou službu místně.

1. Nastavte **Považovat upozornění jako chyby** true a ujistěte se, že nelze publikovat, pokud existují chyby ověření balíčku. **True**

1. Nastavte: **Pomocí portů webového projektu** na **hodnotu True** se ujistěte, že vaše webová role používá stejný port při každém spuštění místně ve službě IIS Express.

1. Na panelu nástrojů sady Visual Studio vyberte **Uložit**.

## <a name="next-steps"></a>Další kroky
- [Konfigurace projektu Azure pomocí více konfigurací služeb](vs-azure-tools-multiple-services-project-configurations.md)
