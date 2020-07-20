from bson.objectid import ObjectId
from mongoengine.fields import BooleanField
from mongoengine.fields import Document
from mongoengine.fields import EmbeddedDocument
from mongoengine.fields import EmbeddedDocumentField
from mongoengine.fields import EmbeddedDocumentListField
from mongoengine.fields import ListField
from mongoengine.fields import ObjectIdField
from mongoengine.fields import StringField
from mongoengine.fields import DictField



class Adilog(Document):
    currentNode = StringField(required=False)
    complete = BooleanField(default=False)
    nbkid = StringField(required=False)
    username = StringField(required=False) 
    parameters =  ListField (default=[])     
    missingParameters =  ListField (default=[])
    intent = DictField(required=False)
    intent_score = StringField(required=False)
    context = StringField(required=False)
    input =  StringField(required=False)
    speechResponse = ListField (default=[])  
    



adilog = Adilog()
            adilog.complete = request_json.get("complete")
            adilog.currentNode = request_json.get("currentNode")
            adilog.intent = result_json["intent"]
            adilog.missingParameters = request_json.get("missingParameters")
            adilog.nbkid = request_json.get("nbkid")
            adilog.parameters = result_json["parameters"]
            #adilog.intent_score = result_json["intent"].confidence
            #adilog.speechResponse = result_json["speechResponse"][0]
            adilog.username = result_json["username"]
            adilog.save()