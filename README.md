# AFNetworking3.0
AFNetworking3.0链式编程封装
```
////get和post请求数据设置缓存类型 与缓存时间
[[AFNetAPIClient sharedJsonClient].setRequest(@"user/getbyimusername/").RequestType(Get).Cachetype(WYQHTTPClientReloadIgnoringLocalCacheData).time(60).Parameters(nil) startRequestWithSuccess:^(NSURLSessionDataTask *task, id responseObject) {
NSLog(@"成功");
} progress:^(NSProgress *progress) {
NSLog(@"1111");
} failure:^(NSURLSessionDataTask *task, NSError *error) {
NSLog(@"bu成功");
}];



[[AFNetAPIClient sharedJsonClient].setRequest(@"user/getbyimusername/").RequestType(Post).Parameters(nil) startRequestWithSuccess:^(NSURLSessionDataTask *task, id responseObject) {
NSLog(@"成功");
} progress:^(NSProgress *progress) {
NSLog(@"1111");
} failure:^(NSURLSessionDataTask *task, NSError *error) {
NSLog(@"bu成功");
}];

//上传图片
UIImage *img = [UIImage imageNamed:@"1"];

NSData *data = UIImageJPEGRepresentation(img, 0.5);

NSDictionary *dic = @{
@"timestamp" : @"1457403110",
@"file"      : data,
@"xtype"     :@"bang_album",
@"token"     : @"8a3dead8022c6c85248efca767c9ecfaf8836617"


};
[[AFNetAPIClient sharedJsonClient].setRequest(@"upload.php").Parameters(dic).filedata(data).name(@"Filedata").filename(@"Filedata.jpg").mimeType(@"image/jpeg") uploadfileWithSuccess:^(NSURLSessionDataTask *task, id responseObject) {
NSLog(@"成功");
} progress:^(NSProgress *progress) {
NSLog(@"1111");
} failure:^(NSURLSessionDataTask *task, NSError *error) {
NSLog(@"bu成功");
}];

////下载文件
[[AFNetAPIClient sharedJsonClient].setRequest(@"http://120.25.226.186:32812/resources/videos/minion_02.mp4") downloadWithSuccess:^(NSURLResponse *response, NSURL *filePath) {
NSLog(@"成功");
} progress:^(NSProgress *progress) {
NSLog(@"1111-%f",progress.fractionCompleted);
} failure:^(NSURLSessionDataTask *task, NSError *error) {
NSLog(@"bu成功");
}];
```
