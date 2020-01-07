---
title: Přidání kontextových parametrů k parametrům spuštění zátěžového testu
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75584475"
---
# <a name="how-to-add-context-parameters-to-a-load-test-run-setting"></a>Postupy: Přidání kontextových parametrů spuštění zátěžového testu

Po vytvoření zátěžového testu s použitím **nového Průvodce zátěžovým testem**, můžete použít **editoru zátěžového testu** Chcete-li změnit vlastnosti scénářů pro splnění potřebám a cílům testování.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Úplný seznam vlastností parametrů spuštění a jejich popis najdete v tématu [zátěžového testu spusťte nastavení](../test/load-test-run-settings-properties.md).

Můžete vytvořit kontext parametry se mají použít v rámci zátěžového testu pomocí editoru zátěžových testů parametry běhu. Parametry kontextu umožňují parametrizovat řetězec.

Předpokládejme, že váš zátěžový test obsahuje test výkonnosti webu, která již používá adresy URL parametry webového serveru pomocí parametru kontextu. Můžete přidat kontextový parametr pro spuštění, který používá stejnou hodnotu pro název jako ten, který se používá v testu výkonnosti webu zátěžového testu. Při spuštění zátěžového testu to bude mapovat testu výkonnosti webu na jiný server. Například pokud váš zátěžový test obsahuje test výkonnosti webu, který používá parametru kontextu s názvem Webový_server1 názvu v adrese URL webového serveru. Pokud potom zadáte parametr kontextu v zátěžovém testu, který je také název Webový_server1 parametry běhu, zátěžový test použije kontextového parametru, který jste přiřadili v spuštění zátěžového testu. Aby se vyjasnilo, pokud test výkonnosti webu v zátěžovém testu používá stejný název parametru kontextu jako kontextový parametr v zátěžovém testu, přepíše kontextový parametr v zátěžovém testu kontextového parametru, který se používá v testu výkonnosti webu.

> [!WARNING]
> Dejte pozor, abyste přepsat neúmyslně kontextového parametru testu výkonnosti webu, při použití kontextových parametrů v nastavení spuštění. Nepoužívejte stejné názvy parametrů kontextu, pokud je to záměrně.

Pokud přiřadíte hodnotu kontextového parametru webový_server1 `http://CorporateStagingWebServer`, pak můžete použít `WebServer1` v průběhu zátěžového testu a snadno a změňte hodnotu na jiný webový server kdykoli.

Kromě toho přiřazením různých hodnot do parametru kontextu za použití stejného názvu v různých spuštění zátěžového testu můžete spustit zátěžový test s použitím různých prostředích:

- Nastavení spuštění podnikové pracovní Webový Server: kontextový parametr s názvem `WebServer1=http://CorporateStagingWebServer`

- Nastavení spuštění podnikové produkční webový Server: The kontextového parametru, který má název `WebServer1=http://CorporateProductionWebServer`

  **Změna nastavení spuštění z příkazového řádku**

  Pokud chcete použít různé parametry spuštění z příkazového řádku využít tak strategii kontextových parametrů, použijte následující příkazy:

  **Set Test.UseRunSetting= CorporateStagingWebServer**

  \- a -

  **mstest /testcontainer:loadtest1.loadtest**

## <a name="to-add-a-context-parameter-to-a-run-setting"></a>Chcete-li přidat kontextový parametr k parametrům spuštění

1. Otevřete zátěžový test.

2. Rozbalte **parametrů běhu** složku ve stromu zátěžového testu v editoru zátěžového testu.

3. Klikněte pravým tlačítkem na konkrétní parametry běhu pro který chcete přidat kontextový parametr a klikněte na tlačítko **přidat kontextový parametr**.

     Nový parametr kontextu se přidá do **kontextových parametrů** složky v **parametrů běhu** složku ve stromu zátěžového testu.

     -nebo-

     Pokud běh nastavení už obsahuje **kontextových parametrů** složky, můžete pravým tlačítkem myši a klikněte na tlačítko **přidat kontextový parametr**.

4. V **vlastnosti** okna, změňte hodnotu **název** podle potřeby (například Webový_server1). V **vlastnosti** okno Změnit **hodnotu** pro parametr, který chcete použít (například `http://CorporateStagingWebServer`).

5. (Volitelné) Opakujte kroky 3 až 5 a použijte jiný řetězec pro **hodnotu** vlastnosti (například `http://CorporateProductionWebServer`).

6. Zvolte, které spustit nastavení, které mají být aktivní. Otevřete místní nabídku běhu a zvolte **nastavit jako aktivní**.

## <a name="see-also"></a>Viz také:

- [Konfigurace parametrů spuštění zátěžového testu](../test/configure-load-test-run-settings.md)
