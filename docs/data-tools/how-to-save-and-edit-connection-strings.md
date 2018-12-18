---
title: 'Postupy: Ukládání a upravování připojovacích řetězců'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f8ef3a2c-029c-423b-9d9e-a4f1add4f640
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 050d5f7bcda86890642a5bef10fa04d2c12b4203
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089228"
---
# <a name="how-to-save-and-edit-connection-strings"></a>Postupy: ukládání a upravování připojovacích řetězců
Připojovací řetězce v sadě Visual Studio aplikace jsou uložené v konfiguračním souboru aplikace (také označované jako nastavení aplikace) nebo pevně přímo v aplikaci. Ukládání připojovacích řetězců v konfiguračním souboru aplikace zjednodušuje správu vaší aplikace. Pokud je potřeba změnit připojovací řetězec, můžete je aktualizovat v souboru nastavení aplikace (na rozdíl od nutnosti změnit ve zdrojovém kódu a překompilování aplikace).

Ukládání citlivých informací (například heslo) v připojovacím řetězci může ovlivnit zabezpečení vaší aplikace. Připojovací řetězce, které jsou uloženy do konfiguračního souboru aplikace nejsou zašifrované nebo matoucí, takže je možné získat přístup k souboru a zobrazte její obsah. Pomocí integrované zabezpečení systému Windows je bezpečnější způsob, jak řídit přístup k databázi.

Pokud není rozhodnete použít integrované zabezpečení systému Windows a vaše databáze vyžaduje zadání uživatelského jména a hesla, je možné vynechat z připojovacího řetězce, ale aplikace bude vyžadovat poskytnout tyto informace se úspěšně připojit k databázi. Můžete například vytvořit dialogové okno se zobrazí výzvu pro tyto informace a dynamicky vytvoří připojovací řetězec za běhu. Zabezpečení stále může být problém, pokud je zachycen informace na cestě k databázi.
Další informace najdete v tématu [chrání informace o připojení](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="to-save-a-connection-string-from-within-the-data-source-configuration-wizard"></a>Chcete-li uložit připojovacího řetězce z v rámci Průvodce konfigurací zdroje dat
V **Průvodce konfigurací zdroje dat**, vyberte možnost pro uložení připojení na **uložit připojovací řetězec do konfiguračního souboru aplikace** stránky.

## <a name="to-save-a-connection-string-directly-into-application-settings"></a>Připojovací řetězec uložit přímo do nastavení aplikace
1. V **Průzkumníku řešení**, dvakrát klikněte na **Můj projekt** ikona (Visual Basic) nebo **vlastnosti** ikona (C#) Chcete-li otevřít **Návrhář projektu** .
1. Vyberte **nastavení** kartě.
1. Zadejte **název** pro připojovací řetězec. Při přístupu k připojovací řetězec v kódu odkazovat tento název.
1. Nastavte **typ** k (**připojovací řetězec**).
1. Ponechte **oboru** nastavena na **aplikace**.
1. Zadejte připojovací řetězec do **hodnotu** pole, nebo klikněte na tlačítko **třemi tečkami** tlačítko (...) v **hodnotu** pole, které chcete otevřít **vlastnosti připojení** dialogové okno vytvořit připojovací řetězec.

## <a name="edit-connection-strings-stored-in-application-settings"></a>Upravit připojovací řetězce, které jsou uložené v nastavení aplikace
Můžete upravit informace o připojení, který je uložený v nastavení aplikace pomocí **Návrhář projektu**.

### <a name="to-edit-a-connection-string-stored-in-application-settings"></a>Chcete-li upravit připojovací řetězec uložený v nastavení aplikace
1. V **Průzkumníku řešení**, dvakrát klikněte na **Můj projekt** ikona (Visual Basic) nebo **vlastnosti** ikona (C#) Chcete-li otevřít **Návrhář projektu** .
1. Vyberte **nastavení** kartě.
1. Vyhledejte připojení, které chcete upravit a vyberte text v **hodnotu** pole.
1. Upravit připojovací řetězec v **hodnotu** pole, nebo klikněte na tlačítko **třemi tečkami** tlačítko (...) v **hodnotu** pole, které chcete upravit připojení s **připojení Vlastnosti** dialogové okno.

## <a name="edit-connection-strings-for-datasets"></a>Upravit připojovací řetězce pro datové sady
Můžete upravit informace o připojení pro každý TableAdapter v datové sadě.

### <a name="to-edit-a-connection-string-for-a-tableadapter-in-a-dataset"></a>Chcete-li upravit připojovací řetězec pro TableAdapter v datové sadě
1. V **Průzkumníku řešení**, dvakrát klikněte na datovou sadu (**XSD** soubor), má připojení, které chcete upravit.
1. Vyberte **TableAdapter** nebo dotaz, který má připojení, které chcete upravit.
1. V **vlastnosti** okno, rozbalte **připojení uzlu**.
1. Pokud chcete rychle upravit připojovací řetězec, upravte **ConnectionString** vlastnost, nebo klikněte na šipku dolů na **připojení** vlastnost a zvolte **nové připojení**.

## <a name="security"></a>Zabezpečení
Ukládání citlivých informací (například heslo) v připojovacím řetězci může ovlivnit zabezpečení vaší aplikace. Pomocí integrované zabezpečení systému Windows je bezpečnější způsob, jak řídit přístup k databázi.
Další informace najdete v tématu [chrání informace o připojení](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="see-also"></a>Viz také:

- [Přidání připojení](../data-tools/add-new-connections.md)