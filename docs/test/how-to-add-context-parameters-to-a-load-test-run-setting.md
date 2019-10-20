---
title: Přidání kontextových parametrů do nastavení spuštění zátěžového testu
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, run settings, context parameters
- load tests, context parameters
ms.assetid: a8a0b97e-8040-4711-85ab-36548b130ed2
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e630bfccb1741e3b194b6be4c6f8cdb065d8b942
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664862"
---
# <a name="how-to-add-context-parameters-to-a-load-test-run-setting"></a>Postupy: Přidání kontextových parametrů do nastavení běhu zátěžového testu

Po vytvoření zátěžového testu pomocí **nového Průvodce zátěžovým testem**můžete pomocí **Editor zátěžového testu** změnit vlastnosti scénářů tak, aby vyhovovaly vašim požadavkům na testování a cílům.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Úplný seznam vlastností parametrů spuštění a jejich popis naleznete v tématu [Vlastnosti nastavení běhu zátěžového testu](../test/load-test-run-settings-properties.md).

Můžete vytvořit kontextové parametry pro použití v nastavení spuštění zátěžového testu pomocí Editor zátěžového testu. Kontextové parametry umožňují parametrizovat řetězec.

Předpokládejme, že váš zátěžový test obsahuje test výkonnosti webu, který již používá parametrizovanou adresu URL webového serveru pomocí parametru kontextu. Můžete přidat kontextový parametr do nastavení spuštění zátěžového testu, které používá stejnou hodnotu názvu jako ta, která se používá v testu výkonnosti webu. Dojde k mapování testu výkonnosti webu na jiný server při spuštění zátěžového testu. Například pokud zátěžový test zahrnuje test výkonnosti webu, který používá kontextový parametr s názvem webserver1 pro název webového serveru v adrese URL. Pokud pak zadáte kontextový parametr v nastavení spuštění zátěžového testu, které se také nazývá webserver1, zátěžový test použije kontextový parametr, který jste přiřadili v nastavení spuštění zátěžového testu. Pro objasnění, pokud test výkonnosti webu v zátěžovém testu používá stejný název kontextového parametru jako kontextový parametr v rámci zátěžového testu, parametr context v zátěžovém testu přepíše kontextový parametr, který se používá v testu výkonnosti webu.

> [!WARNING]
> Buďte opatrní, neúmyslně přepsat kontextový parametr testu výkonnosti webu při použití parametrů kontextu v nastavení spuštění. Nepoužívejte stejné názvy kontextových parametrů, pokud to neuděláte záměrně.

Pokud přiřadíte hodnotu kontextového parametru webserver1 k `http://CorporateStagingWebServer`, můžete použít `WebServer1` v celém zátěžovém testu, a tak snadno změnit hodnotu na jiný webový server.

Kromě toho přiřazením různých hodnot k kontextovému parametru pomocí stejného názvu v různých nastaveních běhu zátěžového testu můžete spustit zátěžový test pomocí různých prostředí:

- Nastavení spuštění podnikového webového serveru: parametr kontextu s názvem `WebServer1=http://CorporateStagingWebServer`

- Nastavení spuštění podnikového webového serveru: parametr kontextu s názvem `WebServer1=http://CorporateProductionWebServer`

  **Změna nastavení spuštění z příkazového řádku**

  Pokud chcete použít jiné parametry spuštění z příkazového řádku, abyste mohli využít strategii kontextového parametru, použijte následující příkazy:

  **Nastavte test. UseRunSetting = CorporateStagingWebServer**

  ani

  **MSTest/testcontainer: LoadTest1. LoadTest**

## <a name="to-add-a-context-parameter-to-a-run-setting"></a>Přidání kontextového parametru do nastavení běhu

1. Otevřete zátěžový test.

2. Rozbalte složku **parametry spuštění** ve stromu zátěžového testu v Editor zátěžového testu.

3. Klikněte pravým tlačítkem na konkrétní nastavení spuštění, ke kterému chcete přidat kontextový parametr, a pak zvolte **Přidat kontextový parametr**.

     Nový kontextový parametr se přidá do složky **parametrů kontextu** ve složce parametrů **běhu** ve stromu zátěžového testu.

     -nebo-

     Pokud již nastavení běhu obsahuje složku **kontextových parametrů** , můžete na něj kliknout pravým tlačítkem myši a vybrat možnost **Přidat kontextový parametr**.

4. V okně **vlastnosti** změňte hodnotu pro **název** podle potřeby (například webserver1). V okně **vlastnosti** změňte **hodnotu** na parametr, který chcete použít (například `http://CorporateStagingWebServer`).

5. Volitelné Opakujte kroky 3 až 5 a použijte jiný řetězec pro vlastnost **Value** (například `http://CorporateProductionWebServer`).

6. Vyberte, která nastavení spuštění mají být aktivní. Otevřete místní nabídku v nastavení spuštění a vyberte **nastavit jako aktivní**.

## <a name="see-also"></a>Viz také:

- [Konfigurovat nastavení běhu zátěžového testu](../test/configure-load-test-run-settings.md)