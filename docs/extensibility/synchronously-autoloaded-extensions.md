---
title: Automaticky synchronně načítaná rozšíření
ms.date: 12/11/2019
ms.topic: conceptual
ms.assetid: 822e3cf8-f723-4ff1-8467-e0fb42358a1f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab62d235fd6ed4e47e765fc23868acd5c56efcb2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699375"
---
# <a name="synchronously-autoloaded-extensions"></a>Automaticky synchronně načítaná rozšíření

Synchronně automaticky načtená rozšíření mají negativní dopad na výkon sady Visual Studio a měla by být převedena tak, aby místo toho používala asynchronní automatické načtení. Ve výchozím nastavení Visual Studio 2019 blokuje synchronně automaticky načtené balíčky z libovolného rozšíření a upozorní uživatele.

![upozornění na kompatibilitu rozšíření](media/extension-compatibility-warning-16-1.png.png)

Můžete:

- Klikněte na **Povolit synchronní automatické načtení,** aby se rozšíření automaticky načítaly. Pokud chcete toto nastavení změnit v možnostech sady Visual Studio, klikněte na Prostředí, potom klikněte na Rozšíření a zaškrtněte políčko Povolit synchronní automatické načtení rozšíření. 

- Klepnutím na **tlačítko Spravovat výkon** otevřete dialogové okno Správce [výkonu,](#performance-manager-dialog) které zobrazuje problémy s výkonem s rozšířeními a okny nástrojů.

- Klikněte na **Nezobrazovat tuto zprávu pro aktuální rozšíření** pro zavření oznámení a zabránit budoucí oznámení z existujících nainstalovaných rozšíření. Pokud přidáte nové rozšíření, které se automaticky načte synchronně, toto oznámení se zobrazí znovu. Budete i nadále dostávat oznámení o dalších funkcích sady Visual Studio.

## <a name="performance-manager-dialog"></a>Dialogové okno Správce výkonu

![dialogové okno správce výkonu](media/performance-manager.png)

Všechna rozšíření, která synchronně načetla všechny balíčky v libovolné uživatelské relace se zobrazí na kartě **Zastaralá rozhraní API.**

* Kliknutím na **další informace o tomto problému** získáte další informace o zastaralá úložiště API.
* Obraťte se na dodavatele rozšíření pro průběh migrace.

## <a name="specify-synchronous-autoload-settings-using-group-policy"></a>Určení synchronního nastavení automatického načtení pomocí zásad skupiny

Správci mohou povolit zásady skupiny a povolit synchronní automatické načítání. Chcete-li tak učinit, nastavte zásady založené na registru na následující klíč:

**HKEY_LOCAL_MACHINE\SOFTWARE\Zásady\Microsoft\VisualStudio\SynchronousAutoload**

Položka = **povoleno**

Hodnota = (DWORD)
* **0** je synchronní automatické načtení není povoleno.
* **1** je synchronní automatické načtení povoleno.

## <a name="extension-authors"></a>Autoři rozšíření
Autoři rozšíření mohou najít pokyny pro migraci balíčků na asynchronní automatické načtení na [migrate to AsyncPackage](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/AsyncPackageMigration).

## <a name="see-also"></a>Viz také
Další informace o synchronních nastaveních automatického načítání v sadě Visual Studio 2019 najdete na stránce [Synchronní chování automatického načítání.](https://devblogs.microsoft.com/visualstudio/updates-to-synchronous-autoload-of-extensions-in-visual-studio-2019/)
