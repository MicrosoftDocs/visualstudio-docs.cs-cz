---
title: 'Chyba: Ladění se nezdařilo, protože ověření integrované Windows není povoleno. | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f56cca9fa637efaa66b6dcab4716d4a1900aa61d
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44278642"
---
# <a name="error-debugging-failed-because-integrated-windows-authentication-is-not-enabled"></a>Chyba: Ladění se nezdařilo, protože integrované ověřování systému Windows není povoleno.
Ověření uživatele, který požaduje ladění nebylo možné kvůli chybě ověřování. Tato situace může nastat, když zkusíte Krokovat s vnořením webovou aplikaci nebo webové služby XML. Jednou z příčin této chyby je, že integrované ověřování Windows není povoleno. Ho Pokud chcete povolit, postupujte podle kroků v "K povolení integrované ověřování Windows."  
  
 Pokud je povoleno integrované ověřování Windows a stále se zobrazí tato chyba, je možné, že k této chybě dojde, protože **ověřování algoritmem Digest pro Windows domény serverů** je povolená. V této situaci byste se obrátit se na správce sítě.  
  
### <a name="to-enable-integrated-windows-authentication"></a>Pokud chcete povolit integrované ověřování Windows  
  
1.  Přihlaste se k webovému serveru pomocí účtu správce.  
  
2.  Klikněte na tlačítko **Start** a potom klikněte na tlačítko **ovládací panely**.  
  
3.  V **ovládací panely**, dvakrát klikněte na panel **nástroje pro správu**.  
  
4.  Dvakrát klikněte na panel **Internetová informační služba**.  
  
5.  Klikněte na uzel webového serveru.  
  
     A **weby** otevře složka pod název serveru.  
  
6.  Můžete nakonfigurovat ověřování pro všechny webové servery nebo pro jednotlivé weby. Konfigurace ověřování pro všechny webové servery, klikněte pravým tlačítkem myši **weby** složku a pak klikněte na tlačítko **vlastnosti**. Chcete-li nakonfigurovat ověřování pro jednotlivé webové stránky, otevřete **weby** složku, klikněte pravým tlačítkem na jednotlivé webové stránky a pak klikněte na tlačítko **vlastnosti**.  
  
     **Vlastnosti** zobrazí dialogové okno.  
  
7.  Klikněte na tlačítko **zabezpečení adresáře** kartu.  
  
8.  V **anonymního přístupu a ověřování** klikněte na tlačítko **upravit**.  
  
     **Metody ověřování** zobrazí dialogové okno.  
  
9. V části **ověřeného přístupu**vyberte **ověření integrované Windows**.  
  
10. Klikněte na tlačítko **OK** zavřete **metody ověřování** dialogové okno.  
  
11. Klikněte na tlačítko **OK** zavřete **vlastnosti** dialogové okno.  
  
12. Zavřít **Internetová informační služba** okna.  
  
### <a name="to-enable-integrated-windows-authentication-in-windows-vistaiis-7"></a>Pokud chcete povolit integrované ověřování Windows ve Windows Vista/IIS 7  
  
1.  Přihlaste se k webovému serveru pomocí účtu správce.  
  
2.  Zapněte ověřování Windows a II6 Kompatibilita správy, pokud jste neudělali dříve, pomocí následujících kroků:  
  
    1.  Klikněte na tlačítko **Start**, klikněte na tlačítko **ovládací panely** a potom klikněte na tlačítko **programy**.  
  
    2.  V části **programy a funkce**, klikněte na tlačítko **Windows zapnout nebo vypnout funkce**.  
  
         Zobrazí se dialogové okno Řízení uživatelských účtů a vás vyzve k zadání oprávnění, abyste mohli pokračovat.  
  
    3.  Klikněte na tlačítko **pokračovat**.  
  
         Zobrazí se dialogové okno funkcí Windows.  
  
    4.  V seznamu funkcí, rozbalte **Internetová informační služba** uzlu.  
  
    5.  V části **Internetová informační služba**, rozbalte **webové služby** uzlu.  
  
    6.  V části **webové služby**, klikněte na tlačítko **zabezpečení**.  
  
    7.  Klikněte na tlačítko **ověřování Windows**.  
  
    8.  V části **Internetová informační služba**, rozbalte **nástroje webové správy** uzlu.  
  
    9. V části **nástroje webové správy**, rozbalte **IIS 6 Management Compatibility** uzel a vyberte **metabáze služby IIS 6 a IIS 6 konfigurace kompatibility** zaškrtávací políčko.  
  
    10. V části **nástroje webové správy**vyberte **konzolu pro správu IIS** a klikněte na tlačítko **OK.**  
  
    11. Restartujte počítač změny se projeví.  
  
3.  Klikněte na tlačítko **Start** a potom klikněte na **ovládací panely**.  
  
4.  Klikněte na tlačítko **klasické zobrazení**a potom dvakrát klikněte na panel **nástroje pro správu**.  
  
5.  V **název** sloupce a dvakrát klikněte na **Správce Internetové informační služby (IIS)**.  
  
6.  V **připojení** sloupce, rozbalte uzel pro váš server.  
  
     A **weby** otevře složka pod název serveru.  
  
7.  Rozbalte **weby** uzel a klikněte na webové stránky, pro kterou chcete povolit integrované ověřování Windows.  
  
8.  Název v prostředním podokně změní název webu, který jste vybrali. V tomto podokně v části **IIS** záhlaví, klikněte dvakrát na **ověřování**.  
  
     Název panelu se změní na **ověřování**.  
  
9. V **ověřování** podokno v **název** sloupce, klikněte pravým tlačítkem na **ověřování Windows** a potom klikněte na tlačítko **povolit**.  
  
10. Zavřít **Správce Internetové informační služby (IIS)** okna.  
  
## <a name="see-also"></a>Viz také  
 [Ladění webových aplikací: Chyby a řešení potíží](../debugger/debugging-web-applications-errors-and-troubleshooting.md)   
 [Ověřování algoritmem Digest Microsoft](http://go.microsoft.com/fwlink/?LinkId=77938)   
 [Spouštění webových aplikací v systému Windows Vista se službou IIS 7.0 a Visual Studio](https://msdn.microsoft.com/Library/262a82ac-dd0e-4096-86c6-fb463e88be66)