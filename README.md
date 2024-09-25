# cmp-im-zh

> fork of [yehuohan/cmp-im-zh](https://github.com/yehuohan/cmp-im-zh)
>
> 更大的码表（但是加载时间也大幅度增加），以满足个人“按词输入”的习惯
>
> 码表源自 [雾凇拼音](https://github.com/iDvel/rime-ice)，小鹤双拼的码表借助 [bcaso/pinyin_to_double_pinyin](https://github.com/bcaso/pinyin_to_double_pinyin/blob/main/dp.py)，由全拼码表转换而来。
>
> 除了更丰富的词库之外，目前直接基于 nvim-cmp 实现的中文输入法与常规输入法在体验上，依然存在的一定差距：
>
> - 按照数字选择候选项，[#1491](https://github.com/hrsh7th/nvim-cmp/pull/1491)
> - 基于云词库的联想和记忆

用于[cmp-im](https://github.com/yehuohan/cmp-im)的中文码表：

- wubi: 86五笔
- pinyin: 拼音
- huge_pinyin: 更大码表的拼音
- huge_flypy: 更大码表的小鹤双拼。小码表可使用 [noearc/cmp-im-flypy](https://github.com/noearc/cmp-im-flypy)

```lua
require('cmp_im').setup{
  tables = require('cmp_im_zh').tables{ 'wubi', 'pinyin' }
}
```

Map标点符号（对于`括号`，`引号`这些，可能会与autopair之类的插件冲突，需要自行临时disable）：

```lua
for lhs, rhs in pairs(require('cmp_im_zh').symbols()) do
    vim.keymap.map('i', lhs, rhs)
end
```

Unmap标点符号：

```lua
for lhs, rhs in pairs(require('cmp_im_zh').symbols()) do
    vim.keymap.del('i', lhs)
end
```

Much thanks for tables from [ZFVimIM#db-samples](https://github.com/ZSaberLv0/ZFVimIM#db-samples).
