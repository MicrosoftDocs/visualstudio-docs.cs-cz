---
title: 'Postupy: Ukládání a upravování připojovacích řetězců'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: f8ef3a2c-029c-423b-9d9e-a4f1add4f640
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e3cb3f832f308edb42967d2fe4485b3d6885022a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85282017"
---
# <a name="how-to-save-and-edit-connection-strings"></a>Postupy: ukládání a úpravy připojovacích řetězců
Připojovací řetězce v aplikacích sady Visual Studio se ukládají do konfiguračního souboru aplikace (také označovaného jako nastavení aplikace) nebo pevně zakódované přímo v aplikaci. Ukládání připojovacích řetězců do konfiguračního souboru aplikace zjednodušuje úlohu správy aplikace. Pokud je třeba připojovací řetězec změnit, můžete ho aktualizovat v souboru nastavení aplikace (na rozdíl od změny ve zdrojovém kódu a znovu kompilovat aplikaci).

Ukládání citlivých informací (například hesla) v rámci připojovacího řetězce může ovlivnit zabezpečení aplikace. Připojovací řetězce uložené do konfiguračního souboru aplikace nejsou zašifrované nebo zašifrované, takže může někdo získat přístup k souboru a zobrazit jeho obsah. Použití integrovaného zabezpečení systému Windows je bezpečnější způsob, jak řídit přístup k databázi.

Pokud se nerozhodnete použít integrované zabezpečení systému Windows a vaše databáze vyžaduje uživatelské jméno a heslo, můžete je vynechat z připojovacího řetězce, ale aplikace bude muset poskytnout tyto informace pro úspěšné připojení k databázi. Můžete například vytvořit dialogové okno, které uživateli vyzve k zadání těchto informací a dynamicky sestavit připojovací řetězec za běhu. Pokud jsou informace zachyceny na cestě k databázi, může být zabezpečení stále problémem.
Další informace najdete v tématu [ochrana informací o připojení](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="to-save-a-connection-string-from-within-the-data-source-configuration-wizard"></a>Uložení připojovacího řetězce v rámci Průvodce konfigurací zdroje dat
V **Průvodci konfigurací zdroje dat**vyberte možnost Uložit připojení na stránce **Uložit připojovací řetězec do konfiguračního souboru aplikace** .

## <a name="to-save-a-connection-string-directly-into-application-settings"></a>Uložení připojovacího řetězce přímo do nastavení aplikace
1. V **Průzkumník řešení**dvakrát klikněte na ikonu **můj projekt** (Visual Basic) nebo na ikonu **vlastnosti** (C#) a otevřete **Návrháře projektu**.
1. Vyberte kartu **Settings** (Nastavení).
1. Zadejte **název** připojovacího řetězce. Při přístupu k připojovacímu řetězci v kódu se podívejte na tento název.
1. Nastavte **typ** na (**připojovací řetězec**).
1. Ponechte **Rozsah** nastavený na **aplikace**.
1. Do pole **hodnota** zadejte připojovací řetězec nebo klikněte na tlačítko se **třemi tečkami** (...) v poli **hodnota** . tím otevřete dialogové okno **Vlastnosti připojení** , ve kterém můžete vytvořit připojovací řetězec.

## <a name="edit-connection-strings-stored-in-application-settings"></a>Upravit připojovací řetězce uložené v nastavení aplikace
Informace o připojení, které jsou uloženy v nastavení aplikace, lze upravit pomocí **Návrháře projektu**.

### <a name="to-edit-a-connection-string-stored-in-application-settings"></a>Úprava připojovacího řetězce uloženého v nastavení aplikace
1. V **Průzkumník řešení**dvakrát klikněte na ikonu **můj projekt** (Visual Basic) nebo na ikonu **vlastnosti** (C#) a otevřete **Návrháře projektu**.
1. Vyberte kartu **Settings** (Nastavení).
1. Vyhledejte připojení, které chcete upravit, a vyberte text v poli **hodnota** .
1. Upravte připojovací řetězec v poli **hodnota** nebo klikněte na tlačítko se **třemi tečkami** (...) v poli **hodnota** a upravte připojení pomocí dialogového okna **Vlastnosti připojení** .

## <a name="edit-connection-strings-for-datasets"></a>Upravit připojovací řetězce pro datové sady
Informace o připojení pro každou TableAdapter můžete upravit v datové sadě.

### <a name="to-edit-a-connection-string-for-a-tableadapter-in-a-dataset"></a>Úprava připojovacího řetězce pro TableAdapter v datové sadě
1. V **Průzkumník řešení**dvakrát klikněte na datovou sadu (soubor **. xsd** ), která má připojení, které chcete upravit.
1. Vyberte **TableAdapter** nebo dotaz, který má připojení, které chcete upravit.
1. V okně **vlastnosti** rozbalte **uzel připojení**.
1. Pokud chcete rychle upravit připojovací řetězec, upravte vlastnost **ConnectionString** nebo klikněte na šipku dolů vlastnosti **připojení** a vyberte **nové připojení**.

## <a name="security"></a>Zabezpečení
Ukládání citlivých informací (například hesla) v rámci připojovacího řetězce může ovlivnit zabezpečení aplikace. Použití integrovaného zabezpečení systému Windows je bezpečnější způsob, jak řídit přístup k databázi.
Další informace najdete v tématu [ochrana informací o připojení](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="see-also"></a>Viz také

- [Přidávání připojení](../data-tools/add-new-connections.md)
