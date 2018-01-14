FROM gcr.io/google-samples/k8sdocs:1.1


VOLUME /k8sdocs

EXPOSE 4000

COPY start.sh /start.sh
WORKDIR /k8sdocs

CMD [ "/start.sh" ]
# For instructions, see http://kubernetes.io/editdocs/
#  docker run -d -v E:/lynzabo.github.io/kubernetes:/k8sdocs -p 4000:4000 lynzabo/k8sdocs:1.1
