---
title: 'Chyba: Brány Firewall v místním počítači | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.firewall.localmachine
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e85c97d5950f71d9552bba944450603e47a5ab49
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31472864"
---
# <a name="error-firewall-on-local-machine"></a>Chyba: Brána firewall v místním počítači
Bránu v místním počítači, počítači, na kterém běží sady Visual Studio, není nastavit a povolit vzdálené ladění. Pro spravované nebo nativní vzdáleného ladění pomocí výchozí přenos, musí být otevřen port TCP 135 pro přenosy modelu DCOM. Sdílení souborů a tiskáren musí být otevřeno a devenv.exe musí být přidaný do seznamu výjimek. Otevírání některé porty protokolu IPSEC může být nutné také.  
  
 Další informace najdete v tématu [vzdálené ladění](../debugger/remote-debugging.md).