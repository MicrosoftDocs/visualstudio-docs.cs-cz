---
title: 'Postupy: Exportování shaderu'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0bd48bf4-9792-4456-a545-e462a2be668d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f4a3aec047238786a60b1261415acccfed521695
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589432"
---
# <a name="how-to-export-a-shader"></a>Postupy: Export shaderu

Tento článek ukazuje, jak pomocí **Návrháře shaderů** exportovat shader jazyka shaderu s řízeným grafem (DGSL), abyste ho mohli používat ve své aplikaci.

## <a name="export-a-shader"></a>Export shaderu

Po vytvoření shaderpomocí pomocí Shader Designer a před použitím v aplikaci, budete muset exportovat ve formátu, který vaše grafické rozhraní API chápe. Shader můžete exportovat různými způsoby, abyste vyhověli různým potřebám.

1. V sadě Visual Studio otevřete soubor **Visual Shader Graph (.dgsl).**

     Pokud nemáte soubor **Visual Shader Graph (.dgsl),** který chcete otevřít, vytvořte soubor, jak je popsáno v [části Postup: Vytvoření základního barevného shaderu](../designers/how-to-create-a-basic-color-shader.md).

2. Na panelu nástrojů **Návrhář shaderu** zvolte **Rozšířený** > **export** > **exportu jako**. Zobrazí se dialogové okno **Exportovat shader.**

3. V rozevíracím seznamu **Uložit jako typ** zvolte formát, který chcete exportovat.

     Zde jsou formáty, které si můžete vybrat:

     **HLSL Pixel Shader (\*.hlsl)** Exportuje shader jako zdrojový kód jazyka HLSL (High Level Shader Language). Tato možnost umožňuje upravit shader později, i když je nasazen v aplikaci. To může usnadnit ladění a opravu kódu na základě problémů koncových uživatelů, ale také usnadňuje uživateli upravovat shader nežádoucími způsoby – například získat nespravedlivou výhodu v konkurenční hře. Může také zvýšit dobu načítání shaderu.

     **Kompilovaný pixelový\*shader ( .cso)** Exportuje shader jako bajtový kód HLSL. Tato možnost umožňuje upravit shader později, i když je nasazen v aplikaci. To může usnadnit ladění a oprava kódu na základě problémů koncových uživatelů, ale protože shader je předem zkompilován, nevznikne další režie runtime při načítání shaderu aplikací. Dostatečně zkušení uživatelé mohou stále upravovat shader nežádoucími způsoby, ale kompilace shaderu to výrazně ztěžuje.

     **Hlavička C++ (\*.h)** Exportuje shader jako hlavičku stylu C, která definuje bajtové pole, které obsahuje bajtový kód HLSL. Tato možnost může být časově náročnější ladění a oprava kódu na základě problémů s koncovým uživatelem, protože aplikace musí být znovu zkompilována, aby otestovala opravu. Protože však tato možnost ztěžuje, i když není nemožné, upravit shader po nasazení v aplikaci, představuje největší potíže pro uživatele, který chce upravit shader nežádoucími způsoby.

4. Do pole Se seznamem **Název souboru** zadejte název exportovaného shaderu a pak zvolte tlačítko **Uložit.**

## <a name="see-also"></a>Viz také

- [Postupy: Vytvoření shaderu základní barvy](../designers/how-to-create-a-basic-color-shader.md)
- [Návrhář shaderu](../designers/shader-designer.md)
