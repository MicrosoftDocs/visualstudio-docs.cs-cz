---
title: 'Chyba: ladění se nezdařilo, protože není povolené integrované ověřování systému Windows | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.webdbg_ntlm_authn_not_enabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
- aspx
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ca4b4ee5bb254f952fb6eb02e255320a337f657c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737802"
---
# <a name="error-debugging-failed-because-integrated-windows-authentication-is-not-enabled"></a>Chyba: Ladění se nezdařilo, protože integrované ověřování systému Windows není povoleno.
Ověření uživatele, který požádalo o ladění, se zabránilo chybou ověřování. Tato situace může nastat při pokusu o krokování do webové aplikace nebo webové služby XML. Jednou z příčin této chyby je, že není povolené integrované ověřování systému Windows. Pokud ho chcete povolit, postupujte podle kroků v tématu povolení integrovaného ověřování systému Windows.

 Pokud jste povolili integrované ověřování systému Windows a tato chyba se pořád zobrazuje, je možné, že tato chyba je způsobená tím, že je povolená možnost **ověřování algoritmem Digest pro doménové servery Windows** . V takovém případě byste se měli obrátit na správce sítě.

### <a name="to-enable-integrated-windows-authentication"></a>Povolení integrovaného ověřování systému Windows

1. Přihlaste se k webovému serveru pomocí účtu správce.

2. Klikněte na tlačítko **Start** a poté na příkaz **Ovládací panely**.

3. V **Ovládacích panelech**poklikejte na **Nástroje pro správu**.

4. Dvakrát klikněte na **Internetová informační služba**.

5. Klikněte na uzel webového serveru.

     Pod názvem serveru se otevře složka **webové servery** .

6. Můžete nakonfigurovat ověřování pro všechny weby nebo pro jednotlivé weby. Chcete-li nakonfigurovat ověřování pro všechny weby, klikněte pravým tlačítkem myši na složku **webové servery** a poté klikněte na příkaz **vlastnosti**. Chcete-li nakonfigurovat ověřování pro jednotlivý web, otevřete složku **webové servery** , klikněte pravým tlačítkem myši na jednotlivý web a potom klikněte na příkaz **vlastnosti**.

     Zobrazí se dialogové okno **vlastnosti** .

7. Klikněte na kartu **zabezpečení adresáře** .

8. V části **řízení anonymního přístupu a ověřování** klikněte na **Upravit**.

     Zobrazí se dialogové okno **metody ověřování** .

9. V části **ověřený přístup**vyberte **integrované ověřování systému Windows**.

10. Kliknutím na tlačítko **OK** zavřete dialogové okno **metody ověřování** .

11. Kliknutím na tlačítko **OK** zavřete dialogové okno **vlastnosti** .

12. Zavřete okno **Internetová informační služba** .

### <a name="to-enable-integrated-windows-authentication-in-windows-vistaiis-7"></a>Povolení integrovaného ověřování systému Windows v systému Windows Vista nebo IIS 7

1. Přihlaste se k webovému serveru pomocí účtu správce.

2. Pokud jste to ještě neudělali, zapněte ověřování systému Windows a kompatibilitu správy II6, a to pomocí následujících kroků:

    1. Klikněte na tlačítko **Start**, klikněte na položku **Ovládací panely** a potom klikněte na položku **programy**.

    2. V části **programy a funkce**klikněte na **zapnout nebo vypnout funkce systému Windows**.

         Zobrazí se dialogové okno uživatel Access Control a zobrazí výzvu k pokračování oprávnění.

    3. Klikněte na **pokračovat**.

         Zobrazí se dialogové okno funkce systému Windows.

    4. V seznamu funkcí rozbalte uzel **Internetová informační služba** .

    5. V části **Internetová informační služba**rozbalte uzel **World roztažitelné Web Services** .

    6. V části **webové služby**klikněte na **zabezpečení**.

    7. Klikněte na **ověřování systému Windows**.

    8. V části **Internetová informační služba**rozbalte uzel **Nástroje webové správy** .

    9. V části **Nástroje pro správu webu**rozbalte uzel **Kompatibilita správy služby IIS 6** a zaškrtněte políčko **metabáze služby IIS 6 a kompatibilita konfigurace služby IIS 6** .

    10. V části **Nástroje pro správu webu**vyberte **Konzola pro správu služby IIS** a klikněte na **OK.**

    11. Restartujte počítač, aby se tyto změny projevily.

3. Klikněte na tlačítko **Start** a poté na příkaz **Ovládací panely**.

4. Klikněte na **klasické zobrazení**a potom poklikejte na **Nástroje pro správu**.

5. Ve sloupci **název** a dvakrát klikněte na **Správce služby Internetová informační služba (IIS)** .

6. Ve sloupci **připojení** rozbalte uzel pro váš server.

     Pod názvem serveru se otevře složka **webové servery** .

7. Rozbalte uzel **webové servery** a klikněte na web, pro který chcete povolit integrované ověřování systému Windows.

8. Název prostředního podokna se změní na název webu, který jste vybrali. V tomto podokně pod nadpisem **IIS** dvakrát klikněte na **ověřování**.

     Název podokna se změní na **ověřování**.

9. V podokně **ověřování** ve sloupci **název** klikněte pravým tlačítkem myši na **ověřování systému Windows** a potom klikněte na možnost **Povolit**.

10. Zavřete okno **Správce služby Internetová informační služba (IIS)** .

## <a name="see-also"></a>Viz také:
- [Ladění webových aplikací: Chyby a řešení potíží](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
- [Ověřování zprostředkovatel zabezpečení Microsoft Digest](http://go.microsoft.com/fwlink/?LinkId=77938)
- [Spouštění webových aplikací v systému Windows Vista se službou IIS 7,0 a sadou Visual Studio](https://msdn.microsoft.com/Library/262a82ac-dd0e-4096-86c6-fb463e88be66)