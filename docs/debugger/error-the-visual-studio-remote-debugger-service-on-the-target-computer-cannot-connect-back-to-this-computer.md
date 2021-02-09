---
title: Služba Visual Studio Remote Debugger na cílovém počítači se nemůže znovu připojit k tomuto počítači.
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.service_access_denied_oncallback
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ef556e19946789abb5805727ccc42c1a9230d9af
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871257"
---
# <a name="error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer"></a>Chyba: Služba vzdáleného ladicího programu sady Visual Studio na cílovém počítači se nemůže připojit zpět k tomuto počítači.
Tato chyba znamená, že je služba vzdáleného ladicího programu spuštěna pod uživatelským účtem, který nelze ověřit při pokusu o připojení k počítači, ze kterého provádíte ladění. K této chybě může dojít při vzdáleném ladění pomocí staršího ladicího stroje a vzdálený ladicí program je spuštěn jako služba.

 Následující tabulka ukazuje, jaké účty mají přístup k počítači:

|Scenario|Účet LocalSystem|Účet domény|Místní účty, které mají stejné uživatelské jméno a heslo v obou počítačích|
|-|-|-|-|
|Oba počítače ve stejné doméně|Ano|Ano|Ano|
|Oba počítače v doménách s obousměrným vztahem důvěryhodnosti|Ne|Ne|Ano|
|Jeden nebo oba počítače v pracovní skupině|Ne|Ne|Ano|
|Počítače v různých doménách|Ne|Ne|Ano|

 Dále musí být splněny všechny tyto podmínky:

- Účet, pod kterým spustíte službu Visual Studio Remote Debugger, se musí nacházet jako správce na vzdáleném počítači, aby mohl ladit jakýkoli proces.

- K účtu musí být také udělené `Log on as a service` oprávnění na vzdáleném počítači, který používá nástroj pro správu **místních zásad zabezpečení** .

- Pokud používáte místní účet pro přístup k počítači, musíte spustit službu Visual Studio Remote Debugger pod místním účtem.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Ujistěte se, že je služba Visual Studio Remote Debugger správně nastavená na vzdáleném počítači. Další informace najdete v tématu [vzdálené ladění](../debugger/remote-debugging.md).

2. Spusťte službu vzdáleného ladícího programu pod účtem, který má přístup k hostitelskému počítači ladicího programu, jak je znázorněno v předchozí tabulce.

### <a name="to-add-log-on-as-a-service-privilege"></a>Přidání oprávnění "přihlásit jako službu"

1. V nabídce **Start** klikněte na položku **Ovládací panely**.

2. V Ovládacích panelech vyberte v případě potřeby **klasické zobrazení**.

3. Poklikejte na **Nástroje pro správu**.

4. V okně nástroje pro správu poklikejte na **místní zásady zabezpečení**.

5. V okně **místní nastavení zabezpečení** rozbalte složku **místní zásady** .

6. Klikněte na **přiřazení uživatelských práv**.

7. Ve sloupci **zásada** dvakrát klikněte na Přihlásit se **jako služba** a zobrazte aktuální místní zásady skupiny přiřazení v dialogovém okně **Přihlásit jako službu** .

8. Chcete-li přidat nové uživatele, klikněte na tlačítko **Přidat uživatele nebo skupinu** .

9. Až skončíte s přidáváním uživatelů, klikněte na **OK**.

### <a name="to-work-around-this-error"></a>Chcete-li tuto chybu obejít

- Spusťte Sledování vzdáleného ladění jako aplikaci namísto služby.

## <a name="see-also"></a>Viz také
- [Chyby vzdáleného ladění a řešení potíží](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Vzdálené ladění](../debugger/remote-debugging.md)