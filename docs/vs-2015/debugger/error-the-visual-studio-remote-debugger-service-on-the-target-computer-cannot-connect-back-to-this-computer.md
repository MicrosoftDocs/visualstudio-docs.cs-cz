---
title: 'Chyba: Služba Visual Studio Remote Debugger v cílovém počítači se nemůže připojit zpět k tomuto počítači | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.service_access_denied_oncallback
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 89ecf99d-66bf-4da0-a840-aa95b0be1702
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 80a7de83f118b38d9a3c71f1c7e7febf48e0f5bc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85520507"
---
# <a name="error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer"></a>Chyba: Služba vzdáleného ladicího programu sady Visual Studio na cílovém počítači se nemůže připojit zpět k tomuto počítači.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato chyba znamená, že služba Visual Studio Remote Debugger je spuštěna pod uživatelským účtem, který nelze ověřit při pokusu o připojení k počítači, ze kterého ladíte.  
  
 Následující tabulka ukazuje, jaké účty mají přístup k počítači:  
  
|Scénář|Účet LocalSystem|Účet domény|Místní účty, které mají stejné uživatelské jméno a heslo v obou počítačích|  
|-|-|-|-|-|  
|Oba počítače ve stejné doméně|Ano|Ano|Ano|  
|Oba počítače v doménách s obousměrným vztahem důvěryhodnosti|Ne|Ne|Ano|  
|Jeden nebo oba počítače v pracovní skupině|Ne|Ne|Ano|  
|Počítače v různých doménách|Ne|Ne|Ano|  
  
 Další vylepšení:  
  
- Účet, pod kterým spustíte službu Visual Studio Remote Debugger, se musí nacházet jako správce na vzdáleném počítači, aby mohl ladit jakýkoli proces.  
  
- K účtu musí být také udělené `Log on as a service` oprávnění na vzdáleném počítači, který používá nástroj pro správu **místních zásad zabezpečení** .  
  
- Pokud používáte místní účet pro přístup k počítači, musíte spustit službu Visual Studio Remote Debugger pod místním účtem.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Ujistěte se, že je služba Visual Studio Remote Debugger správně nastavená na vzdáleném počítači. Další informace najdete v tématu [nastavení nástrojů Remote Tools na zařízení](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).  
  
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
 [Chyby vzdáleného ladění a řešení potíží](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Vzdálené ladění](../debugger/remote-debugging.md)
