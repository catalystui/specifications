<!-- یہ ترجمہ ChatGPT کے ذریعے بنایا گیا ہے اور اسے ایک انسانی مترجم سے جائزہ لینا چاہیے۔ -->
<!-- ترجمہ کی تصدیق کے بعد ان سطروں کو pull request میں ہٹا دیں۔ -->

# پروگرامنگ زبانوں کے لیے CatalystUI Verified

پروگرامنگ زبانوں کے لیے CatalystUI Verification دستاویزات میں خوش آمدید۔

**پروگرامنگ زبانوں کے لیے CatalystUI Verified** اس بات کی نشاندہی کرتا ہے کہ ایک پروگرامنگ زبان کا CatalystUI ٹیم نے جائزہ لیا ہے اور اسے CatalystUI سے مطابقت رکھنے والے نظاموں کو ظاہر کرنے کے لیے مطلوب بنیادی ڈیٹا نمائندگیوں اور ربطی ساختوں کی فراہمی کے قابل پایا ہے۔

یہ تصدیق پروگرامنگ زبانوں کی عمومی درجہ بندی نہیں ہے۔ یہ فیصلہ نہیں کرتی کہ کوئی زبان دوسری سے بہتر، تیز، آسان، نئی، زیادہ مقبول، یا زیادہ لطف بخش ہے۔ اس کے بجائے، یہ پہچانتی ہے کہ آیا زبان CatalystUI Verification کے لیے مطلوب specifications کے لیے ایک مستحکم اور عملی بنیاد فراہم کرتی ہے یا نہیں۔

آسان الفاظ میں، یہ تصدیق پوچھتی ہے کہ آیا ایک پروگرامنگ زبان وہ بنیادی ڈیٹا اور تعلقات درست طور پر ظاہر کر سکتی ہے جن پر CatalystUI انحصار کرتا ہے۔

## مقصد

پروگرامنگ زبانیں ہر CatalystUI implementation کے نیچے نمائندگی کی بنیاد بناتی ہیں۔ کسی framework، library، runtime، application، یا service کے CatalystUI Stack کی پیروی کرنے سے پہلے، اسے بنانے کے لیے استعمال ہونے والی زبان ان بنیادی تصورات کو بیان کرنے کے قابل ہونی چاہیے جن پر model انحصار کرتا ہے۔

پروگرامنگ زبانوں کے لیے اس کا بنیادی مطلب دو چیزیں ہیں:

1. زبان بنیادی ڈیٹا کی نمائندگی کرنے کے قابل ہونی چاہیے۔
2. زبان ڈیٹا کے درمیان بنیادی تعلقات کی نمائندگی کرنے کے قابل ہونی چاہیے۔

یہ امور بنیادی CatalystUI specifications کے ذریعے متعین کیے جاتے ہیں۔ FDEFSPEC متوقع بنیادی ڈیٹا نمائندگیوں کو متعین کرتا ہے۔ FRELSPEC ان نمائندگیوں کے درمیان متوقع بنیادی تعلقات کو متعین کرتا ہے، جن میں collections، memory relationships، operations، threading relationships، اور composites شامل ہیں۔

ایک verified programming language developers کو اتنی وضاحت اور control دیتی ہے کہ وہ CatalystUI-compatible systems بنا سکیں، بغیر ان بنیادی تصورات کے لیے نازک، غیر واضح، یا غیر مستحکم workaround پر انحصار کیے جن کی CatalystUI کو ضرورت ہے۔

## Verification کا مطلب

ایک programming language اس وقت **CatalystUI Verified** بنتی ہے جب اس section میں درج specifications کے مقابل اس کا جائزہ لیا جائے اور اسے within spec پایا جائے۔

Programming Language Verification میں review اس بات پر مرکوز ہوتا ہے کہ آیا زبان applicable specifications میں بیان کی گئی foundational requirements کو ظاہر کر سکتی ہے۔ اس کا مطلب یہ نہیں کہ زبان بذاتِ خود CatalystUI implementation ہے۔ اس کا مطلب یہ ہے کہ زبان ایسی مناسب بنیاد فراہم کرتی ہے جس پر CatalystUI-compatible implementations بنائی جا سکتی ہیں۔

کسی زبان کو یہ requirements کسی دوسری زبان ہی کی طرح پوری کرنے کی ضرورت نہیں۔ مختلف زبانیں مختلف syntax، type systems، standard libraries، compilers، runtimes، اور design patterns استعمال کرتی ہیں۔ CatalystUI Verification ان فرقوں کی اجازت دیتی ہے، بشرطیکہ مطلوب concepts واضح، قابل اعتماد، اور مسلسل انداز میں ظاہر کیے جا سکیں۔

## “Within Spec” کا مطلب

جب کسی programming language کو **within spec** سمجھا جاتا ہے تو اس کا مطلب ہے کہ CatalystUI Team نے زبان کا دستی طور پر review کیا ہے اور یہ نتیجہ معقول سمجھا ہے کہ applicable specifications میں بیان کیا گیا مطلوب behavior اس زبان میں ظاہر کیا جا سکتا ہے۔

اس کے لیے ایک سخت implementation pattern ضروری نہیں۔ کوئی زبان requirement کو built-in primitives، standard library features، compiler behavior، runtime behavior، documented guarantees، یا اس زبان کے لیے مناسب کسی دوسرے مستحکم mechanism کے ذریعے پورا کر سکتی ہے۔

Verification کا تعلق specification کے معنی کو ظاہر اور محفوظ رکھنے کی عملی صلاحیت سے ہے، نہ کہ اس بات سے کہ زبان specification text جیسے ہی names، structures، syntax، یا internal design استعمال کرتی ہے یا نہیں۔

## یہ Verification کیوں موجود ہے

CatalystUI کو clarity، consistency، اور انسانوں اور computers کے interaction کی faithful representation کے گرد design کیا گیا ہے۔ Programming languages اہم ہیں کیونکہ وہ طے کرتی ہیں کہ developers حقیقتاً کیا express کر سکتے ہیں، ان systems کو کتنی safely model کیا جا سکتا ہے، اور higher-level implementations کتنی clearly بن سکتی ہیں۔

اگر کوئی زبان required foundational concepts کو stable انداز میں فراہم نہیں کر سکتی تو higher-level CatalystUI implementations پر اعتماد مشکل ہو جاتا ہے۔ Developers کو صرف ایسے ideas express کرنے کے لیے unclear abstractions، unpredictable behavior، fragile dependencies، یا unnecessary rewrites کی طرف دھکیلا جا سکتا ہے جو شروع ہی سے reliable ہونے چاہییں۔

Programming Language Verification اس لیے موجود ہے کہ یہ پہچان سکے کہ کون سی زبانیں CatalystUI work کے لیے کافی مضبوط foundation فراہم کرتی ہیں۔ یہ developers، language designers، اور organizations کو اس بات کی واضح سمجھ دیتی ہے کہ کوئی زبان CatalystUI-compatible systems بنانے کے لیے موزوں ہے یا نہیں۔

## ایک زبان Verified کیسے بنتی ہے

**CatalystUI Verified for Programming Languages** بننے کے لیے کسی زبان کا اس section میں درج specifications کے مقابل review ہونا ضروری ہے۔

عمومی process یہ ہے:

1. applicable CatalystUI specifications کی شناخت کی جاتی ہے۔
2. زبان کا ہر required specification کے مقابل review کیا جاتا ہے۔
3. CatalystUI Team یہ طے کرتی ہے کہ زبان specifications کے intent اور requirements کو پورا کرتی ہے یا نہیں۔
4. اگر زبان within spec پائی جائے تو اسے CatalystUI Verification دی جا سکتی ہے۔
5. Verified ہونے کے بعد زبان [Verified Languages](/verified/) page پر درج کی جا سکتی ہے۔

Review میں official language documentation، standard library behavior، compiler behavior، runtime behavior، implementation examples، test cases، اور وہ دیگر evidence شامل ہو سکتی ہیں جن سے طے کیا جا سکے کہ زبان requirements پوری کرتی ہے یا نہیں۔

Review کے دوران compiler اور runtime behavior کو اس وقت consider کیا جا سکتا ہے جب یہ behavior زبان کے common اور official استعمال کا حصہ ہو۔ تاہم، programming language کو verify کرنا اس زبان کے ecosystem میں ہر compiler، runtime، package، framework، library، application، یا tool کو خود بخود verify نہیں کرتا۔

## Applicable Specifications

اس section میں درج specifications وہ requirements define کرتی ہیں جو Programming Language Verification کے لیے استعمال ہوتی ہیں۔

Programming languages کے لیے active foundation فی الحال درج ذیل specification categories پر centered ہے:

* **FDEFSPEC**، جو foundational data representations define کرتا ہے۔
* **FRELSPEC**، جو data representations کے درمیان foundational relations define کرتا ہے۔

یہ specifications مل کر وہ minimum foundation establish کرتی ہیں جو کسی programming language کے CatalystUI-compatible systems represent کرنے کے لیے required ہے۔

مزید specialized verification categories کے لیے بعد میں additional specifications متعارف کرائی جا سکتی ہیں۔ وہ specifications higher-level implementation، platform، accessibility، internationalization، framework، service، یا runtime requirements define کر سکتی ہیں۔ تاہم وہ later specifications foundation کو replace کرنے کے بجائے اسی پر build کرتی ہیں۔

ایک programming language اس category کے required specifications کو satisfy کر کے verified بنتی ہے۔ اس سے unrelated implementation-specific requirements پوری کرنے کی توقع نہیں کی جاتی، جب تک وہ requirements Programming Language Verification میں شامل نہ کی جائیں۔

## Verification کا دائرہ

Programming Languages کے لیے CatalystUI Verification اس programming language پر apply ہوتی ہے جیسا کہ review کی گئی ہو۔

ایک verified language CatalystUI-compatible development کے لیے مناسب foundation فراہم کرتی ہے۔ یہ guarantee نہیں دیتی کہ اس زبان میں لکھا ہر project CatalystUI کی صحیح پیروی کرتا ہے، اور نہ ہی یہ surrounding ecosystem کو خود بخود verify کرتی ہے۔

الگ tools، libraries، frameworks، runtimes، applications، services، یا implementations کو requested verification category کے مطابق اپنے review کی ضرورت ہو سکتی ہے۔

لہٰذا Programming Language Verification کو foundation check سمجھنا چاہیے۔ یہ confirm کرتی ہے کہ زبان required concepts represent کر سکتی ہے۔ یہ confirm نہیں کرتی کہ زبان کا ہر استعمال ان concepts کو صحیح طور پر apply کرتا ہے۔

## Verification کی Validity

CatalystUI Verification صرف اس وقت programming language کی reviewed state پر apply ہوتی ہے جب verification issue کی جاتی ہے۔

Programming languages کو special case سمجھا جاتا ہے کیونکہ بہت سی languages multiple versions میں compatibility برقرار رکھتی ہیں۔ کوئی language later versions میں اپنی verification برقرار رکھ سکتی ہے جب تک وہ features، primitives، representations، اور behavior کے ساتھ backward compatibility برقرار رکھتی ہے جن پر original review نے انحصار کیا تھا۔

صرف نئے language features verification کو invalidate نہیں کرتے۔ future version کو new review کی ضرورت صرف اس وقت ہو سکتی ہے جب وہ verified foundation کو remove، break، یا substantially change کرے۔

دوسرے الفاظ میں، language کو extend کرنا عموماً ٹھیک ہے۔ verified base کو break کرنا review کا تقاضا کر سکتا ہے۔

## Verified Languages

known verified programming languages کو [Verified Languages](/verified/) page پر الگ درج کیا گیا ہے۔
