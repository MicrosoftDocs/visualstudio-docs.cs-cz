---
title: Řešení potíží
description: Běžné problémy a řešení pro uživatele Sady Visual Studio pro Mac.
ms.topic: troubleshooting
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: CE860D79-E29E-4B93-B094-BE74B35FC1C2
ms.openlocfilehash: 6073e0bf2a601bf5183798a1df4fd835d0b93427
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "74985161"
---
# <a name="troubleshooting"></a>Řešení potíží

## <a name="viewing-logs-in-visual-studio-for-mac"></a>Zobrazení protokolů ve Visual Studiu pro Mac

Protokoly lze nalézt procházením položky nabídky **> Nabídky otevřít adresář protokolu nápovědy,** jak je znázorněno níže:

![Otevřít položku nabídky adresáře protokolu](media/troubleshooting-image1.png)

## <a name="viewing-exceptions"></a>Zobrazení výjimek

Když je výjimka zachycena, zobrazí se bublina výjimky. Chcete-li zobrazit další podrobnosti, vyberte tlačítko **Zobrazit podrobnosti:**

![Zobrazit další podrobnosti o výjimce](media/troubleshooting-image2.png)

Zobrazí se dialogové okno **Zobrazit podrobnosti,** které poskytuje další informace týkající se výjimky:

![Dialogové okno Zobrazit podrobnosti](media/troubleshooting-image3.png)

Důležité části dialogu, které jsou číslovány výše, jsou podrobně popsány níže:

1. Typ výjimky, který zobrazuje úplný název typu výjimky, který je pozorován.
2. Zpráva o výjimce, která zobrazuje hodnotu Message vlastnost objektu výjimky.
3. Vnitřní typ výjimky, který zobrazuje úplný název typu výjimky pro aktuálně vybranou výjimku v zobrazení stromu vnitřní výjimky.
4. Vnitřní zpráva o výjimce zobrazuje hodnotu Vlastnost Message vybrané výjimky ve stromovém zobrazení vnitřní výjimky.
5. Stacktrace zobrazení. To lze sbalit pomocí šipky zpřístupnění a obsahuje položky rámců zásobníku.
6. Příklad položek kódu neuživatelského.
7. Příklad položek kódu uživatele.
8. Zobrazení vlastností, které zobrazuje všechny vlastnosti a pole výjimky. To lze sbalit pomocí šipky zpřístupnění.
9. Zobrazení stromu vnitřní výjimky. Vyberte vnitřní výjimky v tomto zobrazení pomocí kláves nahoru / dolů šipky nebo pomocí myši nebo trackpad.
10. Ve výchozím nastavení je nastavena na to, co **ladicí kód kódu pouze** možnost v nastavení ladicího programu je nastavena na. Toto pole umožní sbalení všech neuživatelských kódů do jednoho řádku v stacktrace.
11. Tlačítko kopírování pro `exception.ToString()` kopírování výstupu do schránky.

Všimněte si, že některé z těchto oddílů jsou viditelné pouze v případě, že výjimka má vnitřní výjimku.

## <a name="see-also"></a>Viz také

- [Prostředky pro řešení chyb IDE (Visual Studio v systému Windows)](/visualstudio/ide/reference/resources-for-troubleshooting-integrated-development-environment-errors)