---
title: 'Postupy: Exportování shaderu'
description: Naučte se používat návrháře shaderů k exportu funkce shaderu orientovaného grafického shaderu, abyste ji mohli použít ve své aplikaci.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 0bd48bf4-9792-4456-a545-e462a2be668d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7f4abcdf5648031be9b76ba3f25e0a8f33d4efba
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930964"
---
# <a name="how-to-export-a-shader"></a>Postupy: Export shaderu

Tento článek ukazuje, jak pomocí **Návrháře shaderu** exportovat shader DGSL (Direct Graph shader Language), abyste ho mohli použít ve své aplikaci.

## <a name="export-a-shader"></a>Export shaderu

Po vytvoření shaderu pomocí Návrháře shaderu a před jeho použitím v aplikaci je nutné ho exportovat ve formátu, který vaše grafické rozhraní API zná. Shader můžete vyexportovat různými způsoby pro splnění různých potřeb.

1. V aplikaci Visual Studio otevřete soubor **grafu Visual shader (. DGSL)** .

     Pokud nemáte soubor **grafu vizuálních shaderů (. DGSL)** otevřený, vytvořte ho tak, jak je popsáno v tématu [How to: Create a Basic Color shader](../designers/how-to-create-a-basic-color-shader.md).

2. Na panelu nástrojů **Návrháře shaderů** vyberte **Rozšířené** export exportu  >    >  **jako**. Zobrazí se dialogové okno **exportovat shader** .

3. V rozevíracím seznamu **Uložit jako typ** vyberte formát, který chcete exportovat.

     Můžete zvolit následující formáty:

     **HLSL pixel shader ( \* . HLSL)** exportuje shader jako zdrojový kód HLSL (High Level shader Language). Tato možnost umožňuje změnit shader později i po jeho nasazení v aplikaci. To může zjednodušit ladění a opravování kódu na základě problémů koncových uživatelů, ale také usnadňuje uživateli upravit váš shader nežádoucím způsobem – například pro získání nerovné výhody v konkurenční hře. Může také prodloužit dobu načítání shaderu.

     **Kompilovaný pixel shader ( \* . CSO)** exportuje shader jako bytového kódu HLSL. Tato možnost umožňuje změnit shader později i po jeho nasazení v aplikaci. To může zjednodušit ladění a opravování kódu na základě problémů koncových uživatelů, ale vzhledem k tomu, že shader je předem zkompilován, neposkytuje dodatečnou režii za běhu, když je shader načten aplikací. Dostatečně zkušení uživatelé mohou i nadále upravovat shader nevyžádanými způsoby, ale kompilování shaderu to dělá mnohem obtížnější.

     **Záhlaví C++ ( \* . h)** exportuje shader jako záhlaví ve stylu jazyka C, které definuje bajtové pole obsahující HLSL bajt. Tato možnost může být časově náročná na ladění a opravování kódu na základě problémů koncových uživatelů, protože aplikace musí být znovu zkompilována pro otestování opravy. Vzhledem k tomu, že tato možnost je obtížné, ale není nemožné, pro úpravu shaderu po jeho nasazení v aplikaci, prezentuje největší obtíže uživateli, který chce změnit shader nevyžádanými způsoby.

4. V poli se seznamem **název souboru** zadejte název exportovaného shaderu a pak klikněte na tlačítko **Uložit** .

## <a name="see-also"></a>Viz také

- [Postupy: Vytvoření shaderu základní barvy](../designers/how-to-create-a-basic-color-shader.md)
- [Návrhář shaderu](../designers/shader-designer.md)
