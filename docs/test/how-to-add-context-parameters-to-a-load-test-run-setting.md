---
title: Přidání kontextových parametrů do nastavení spuštění zátěžového testu
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, run settings, context parameters
- load tests, context parameters
ms.assetid: a8a0b97e-8040-4711-85ab-36548b130ed2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 05efbba005a9455af3b9d2e8755b580a8af30d0a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75584475"
---
# <a name="how-to-add-context-parameters-to-a-load-test-run-setting"></a>Postup: Přidání parametrů kontextu do nastavení spuštění zátěžového testu

Po vytvoření zátěžového testu pomocí **Průvodce novým zátěžovými testy**můžete pomocí **Editoru zátěžového testu** změnit vlastnosti scénářů tak, aby vyhovovaly vašim potřebám a cílům testování.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Úplný seznam vlastností nastavení spuštění a jejich popisy naleznete v tématu [Načtení vlastností nastavení spuštění testu](../test/load-test-run-settings-properties.md).

Pomocí editoru zátěžového testu můžete vytvořit parametry kontextu, které se použijí v nastavení spuštění zátěžového testu. Parametry kontextu umožňují parametrizovat řetězec.

Předpokládejme, že zátěžový test obsahuje test výkonu webu, který již používá parametrizovanou adresu URL webového serveru pomocí parametru kontextu. Parametr kontextu můžete přidat do nastavení spuštění zátěžového testu, které používá stejnou hodnotu názvu jako ta, která se používá v testu výkonu webu. To bude mapovat test výkonu webu na jiný server při spuštění zátěžového testu. Například pokud zátěžový test obsahuje test výkonu webu, který používá parametr kontextu s názvem WebServer1 pro název webového serveru v adrese URL. Pokud pak zadáte parametr kontextu v nastavení spuštění zátěžového testu, který je také pojmenován WebServer1, zátěžový test použije parametr kontextu, který jste přiřadili v nastavení spuštění zátěžového testu. Chcete-li objasnit, pokud test výkonu webu v zátěžovém testu používá stejný název parametru kontextu jako parametr kontextu v zátěžovém testu, parametr kontextu v zátěžovém testu přepíše parametr kontextu, který se používá v testu výkonu webu.

> [!WARNING]
> Dávejte pozor, abyste neúmyslně přepsat parametr kontextu testu výkonu webu při použití parametrů kontextu v nastavení spuštění. Nepoužívejte stejné názvy parametrů kontextu, pokud to neuděláte úmyslně.

Pokud přiřadíte hodnotu parametru kontextu `http://CorporateStagingWebServer`Webserver1 `WebServer1` , můžete ji použít v celém zátěžovém testu a tím kdykoli snadno změnit hodnotu na jiný webový server.

Navíc přiřazením různých hodnot parametru kontextu pomocí stejného názvu v různých nastaveních spuštění zátěžového testu můžete spustit zátěžový test pomocí různých prostředí:

- Nastavení spuštění podnikového pracovního webového serveru: Parametr context s názvem`WebServer1=http://CorporateStagingWebServer`

- Nastavení spuštění podnikového produkčního webového serveru: Parametr Context s názvem`WebServer1=http://CorporateProductionWebServer`

  **Změna nastavení spuštění z příkazového řádku**

  Chcete-li použít jiné nastavení spuštění z příkazového řádku, abyste využili výhod strategie parametrů kontextu, použijte následující příkazy:

  **Set Test.UseRunSetting= CorporateStagingWebServer**

  -a-

  **mstest /testcontainer:loadtest1.loadtest**

## <a name="to-add-a-context-parameter-to-a-run-setting"></a>Přidání parametru kontextu do nastavení spuštění

1. Otevřete zátěžový test.

2. Rozbalte složku **Spustit nastavení** ve stromu zátěžového testu v Editoru zátěžového testu.

3. Klepněte pravým tlačítkem myši na konkrétní nastavení spuštění, do kterého chcete přidat parametr kontextu, a pak zvolte **Přidat parametr kontextu**.

     Nový parametr kontextu je přidán do složky **Parametry kontextu** ve složce **Spustit nastavení** ve stromu zátěžového testu.

     -nebo-

     Pokud nastavení spuštění již obsahuje složku **Kontextové parametry,** můžete na ni klepnout pravým tlačítkem myši a pak zvolit **Přidat kontextový parametr**.

4. V okně **Vlastnosti** změňte podle potřeby hodnotu **Název** (například WebServer1). V okně **Vlastnosti** změňte **hodnotu** na parametr, který `http://CorporateStagingWebServer`chcete použít (například).

5. (Nepovinné) Opakujte kroky 3 až 5 a **Value** pro vlastnost Value `http://CorporateProductionWebServer`použijte jiný řetězec (například).

6. Zvolte, která nastavení spouštějí, chcete-li být aktivní. Otevřete místní nabídku v nastavení běhu a zvolte **Nastavit jako aktivní**.

## <a name="see-also"></a>Viz také

- [Konfigurace nastavení spuštění zátěžového testu](../test/configure-load-test-run-settings.md)
