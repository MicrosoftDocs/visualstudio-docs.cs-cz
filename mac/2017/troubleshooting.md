---
title: Řešení potíží
description: Běžné problémy a řešení pro Visual Studio pro Mac uživatele.
ms.topic: troubleshooting
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: CE860D79-E29E-4B93-B094-BE74B35FC1C2
ms.openlocfilehash: 6073e0bf2a601bf5183798a1df4fd835d0b93427
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74985161"
---
# <a name="troubleshooting"></a>Řešení potíží

## <a name="viewing-logs-in-visual-studio-for-mac"></a>Zobrazení protokolů v Visual Studio pro Mac

Protokoly najdete tak, že přejdete do nabídky > otevřete položku v nabídce **adresář protokolu** , jak je znázorněno níže:

![Otevřít položku nabídky adresáře protokolu](media/troubleshooting-image1.png)

## <a name="viewing-exceptions"></a>Zobrazení výjimek

Při zachycení výjimky se zobrazí bublina výjimky. Pokud chcete zobrazit další podrobnosti, vyberte tlačítko **Zobrazit podrobnosti** :

![Zobrazit další podrobnosti o výjimce](media/troubleshooting-image2.png)

Tím se zobrazí dialogové okno **Zobrazit podrobnosti** , ve kterém najdete další informace týkající se výjimky:

![Zobrazit dialog podrobností](media/troubleshooting-image3.png)

Důležité části dialogu, které jsou očíslovány nahoře, jsou podrobněji popsány níže:

1. Typ výjimky, která zobrazuje úplný název typu výjimky, který je pozorován.
2. Zpráva o výjimce, která zobrazuje hodnotu vlastnosti zprávy objektu Exception.
3. Typ vnitřní výjimky, který zobrazuje úplný název typu výjimky pro aktuálně vybranou výjimku v zobrazení stromu vnitřní výjimky.
4. Zpráva o vnitřní výjimce zobrazuje hodnotu vlastnosti zpráva vybrané výjimky v zobrazení stromu vnitřních výjimek.
5. Zobrazení trasování zásobníku. Dá se sbalit pomocí šipky oznámení a obsahuje položky rámců zásobníku.
6. Příklad neuživatelových záznamů kódu.
7. Příklad záznamů uživatelského kódu.
8. Zobrazení vlastností, které zobrazuje všechny vlastnosti a pole výjimky. Dá se sbalit pomocí šipky pro zveřejnění.
9. Zobrazení stromu vnitřních výjimek. V tomto zobrazení vyberte vnitřní výjimky pomocí šipek nahoru a dolů nebo pomocí myši nebo trackpadu.
10. Ve výchozím nastavení je tato možnost nastavena na hodnotu možnosti **ladit pouze kód projektu** v nastavení ladicího programu. Zaškrtnutí tohoto políčka umožní, aby se všechny neuživatelský kód v trasování zásobníku sbalovat na jeden řádek.
11. Tlačítko Kopírovat, které zkopíruje `exception.ToString()` výstup do schránky.

Všimněte si, že některé z těchto oddílů jsou viditelné pouze v případě, že výjimka má vnitřní výjimku.

## <a name="see-also"></a>Viz také

- [Prostředky pro řešení potíží s chybami IDE (Visual Studio ve Windows)](/visualstudio/ide/reference/resources-for-troubleshooting-integrated-development-environment-errors)